---
name: invisible-performance
description: Make a web app faster, smoother, and less laggy with ZERO visible UI changes. Use when the user says "make it faster but change nothing", "less laggy", "smoother", "optimize performance", or "no visible changes". Every fix must be pixel-identical and behavior-identical; refuse any optimization that alters what users see, even slightly.
---

# Invisible Performance

Mission: cut jank, memory, and load time while preserving 100% of the visible
UI. The test for every change: could a user with two monitors side by side
tell before/after apart? If yes, or even maybe, do not make the change.
Report it as an option instead.

## The audit, in priority order

Work through these categories. Each is invisible by construction.

### 1. Compositor layer explosion (top cause of scroll jank)

- `grep -n "will-change" **/*.css`. For each hit ask: how many instances
  exist, and does it animate continuously?
  - Many instances (letters, words, list items, cards) + animates only
    sometimes → REMOVE. Motion libraries add the hint during animation
    themselves. Permanent hints on N elements = N GPU layers forever.
  - One instance, continuously animating (custom cursor, scroll traveler,
    infinite spinner) → KEEP.
  - `will-change` on non-compositable properties (color, text-shadow,
    filter lists) → REMOVE, it only forces layers without helping.
- `will-change` is a hint, never a visual property. Removing it is always
  pixel-identical.

### 2. Paint-expensive animations that can be re-implemented identically

- Animated `filter: blur()` is the #1 lag source. You cannot remove a blur
  the design depends on (visible), but you CAN:
  - stop animating blur on elements whose blur is fully transparent at rest
    (animate opacity of a pre-blurred layer instead),
  - reduce simultaneous blurred elements by checking whether several share a
    parent that could carry one blur.
  - If the blur must go to fix lag, that is a VISIBLE change: surface it,
    don't do it.
- `box-shadow`/`background` transitions on hover of large surfaces:
  pre-render as an ::after with opacity transition (identical pixels,
  compositor-only).

### 3. JavaScript main-thread work

- Bundle: `optimizePackageImports` for barrel-exporting libs (motion,
  lucide, lodash-like). Check with the build's chunk output.
- `next/dynamic` with `ssr: false` for heavy client-only components that are
  BELOW the fold and draw nothing until interaction/scroll (canvas scenes,
  maps, charts). Above-the-fold or SSR-rendered content: never, it would
  flash.
- Event listeners: one shared window pointermove/scroll listener with an
  rAF-batched subscriber set, not one per component instance.
- rAF loops: pause on IntersectionObserver exit AND document.hidden. Zero
  allocations per frame (reuse arrays, cache gradients, Path2D batches).
- Avoid getBoundingClientRect / layout reads inside per-event handlers when
  the value can be read once (but beware: caching a rect that changes with
  scroll-while-hovering CAN change behavior; verify identical).
- React: memo only where re-renders provably happen with unchanged props
  (profile first, don't scatter memo).

### 4. Network & assets

- Media: lazy-load below-fold images (`loading="lazy" decoding="async"`),
  pause offscreen videos, `preload` posters for hero media.
- Fonts: verify every loaded family/weight is actually referenced in CSS
  before assuming; removing a used one changes rendering (visible!).
- Canvas: cap devicePixelRatio at 2.

### 5. Things that look invisible but are NOT (refuse or flag)

- `content-visibility: auto` — changes scrollbar length and breaks
  measured-geometry effects (scroll-linked SVG paths). Flag as option only.
- Reducing animation durations, spring stiffness, stagger counts, particle
  counts, blur radii, DPR below 2 on hi-dpi — all visible. Never.
- Debouncing/throttling pointer-driven motion — adds perceptible latency.
- Swapping fonts, image formats with different compression artifacts, or
  removing "redundant" decorative layers.
- `preload="metadata"` on an autoplaying video — delays first frame.

## Workflow

1. Inventory: grep for will-change, filter, backdrop-filter, box-shadow
   transitions, rAF loops, scroll/pointer listeners, large client
   components, font loads.
2. Classify each finding: invisible fix / visible trade-off (report only).
3. Apply invisible fixes in small commits-worth of edits.
4. Verify: typecheck, lint, production build. Then run the app and visually
   sweep every affected surface in both themes, hover states included.
5. Report honestly: what got faster and why, what was left alone because it
   would be visible, and where the remaining cost lives (usually the visible
   effects themselves).

## Honest ceiling

Most runtime cost in a motion-heavy site IS the visible design (canvas
scenes, scroll-linked springs, per-word reveals). Invisible optimization
trims real waste around them but cannot make an 60fps-heavy design free.
When the invisible wins are exhausted, say so and list the visible dials the
user could choose to turn, with expected gains. Never turn them yourself.
