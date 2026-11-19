# Accessibility review matrix

Use this for the full practical audit. Apply criteria to actual content and interactions, not merely the source code. WCAG success criteria are normative; the checks below are a practical translation, not a substitute for reading them. Check current [WCAG 2.2](https://www.w3.org/TR/WCAG22/) and [WAI Understanding](https://www.w3.org/WAI/WCAG22/Understanding/) when classifying a failure.

## A. Navigation and operation without a mouse

- From a fresh load, use only keyboard to reach and operate every critical control, including mobile navigation, carousels, accordions, modals, tabs, date pickers, forms, and external links. Test forward and reverse focus, activation, dismissal, and return focus.
- Ensure a visible focus indicator in every state and background; no sticky header, overlay, animation, or off-screen placement obscures the focused control. Verify focus order follows meaning, not visual tricks.
- Check bypass mechanism/skip link or equivalent for repeated navigation, semantic landmarks, sensible heading hierarchy, descriptive links, and no unexpected keyboard trap. A skip link must actually focus or bring the main content into an operable position.
- For custom widgets, compare expected key behavior with the [WAI-ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/). Prefer native HTML controls over custom ARIA when possible. Check state (`expanded`, `selected`, `invalid`, etc.) and name/role/value in the accessibility tree.
- Check non-pointer alternatives for hover-only disclosure, drag-and-drop, swipe, drawing, path gestures, and device-motion controls. Do not rely on a keyboard test of desktop nav to prove mobile menu works.

## B. Perception, color, and vision

- Never use color alone for status, required fields, errors, chart categories, links, availability, or success. Look for text, icons with names, patterns, shape, or other redundant cues. Grayscale/color-vision simulation is a prompt to investigate, not proof of accessibility.
- Measure **actual** foreground/background contrast including gradients, images, transparency, video, focus/hover, placeholder, and overlay states. WCAG 2.2 AA text minimum is generally 4.5:1, or 3:1 for large text; non-text UI boundaries and meaningful graphics generally need 3:1 against adjacent colors. Apply the criterion’s exceptions precisely rather than treating every element alike.
- Check text resize to 200%, reflow at 320 CSS px equivalent (often 400% zoom on a 1280 CSS-px viewport), and increased text spacing. Test loss of content/function, two-dimensional scrolling except content that intrinsically requires it, clipped labels, fixed overlays, and focus occlusion. Do not treat fixed device presets as a substitute for zoom testing.
- Ensure text is real, selectable, and resizable where possible; avoid information inside images of text. Verify icon-only controls and image links have meaningful accessible names, and decorative images are ignored. Informative images need task-appropriate alternatives, not filename or SEO stuffing.
- Check meaningful video/audio for captions, transcripts, and audio description where applicable. Verify controls are keyboard accessible. Avoid surprise autoplay and seizure-risk flashes.

## C. Structure, screen readers, and dynamic content

- Check page title, declared language, one logical primary heading hierarchy, landmarks, lists, tables with headers where appropriate, and link/button roles that match behavior. Test reading and control navigation, not just whether text appears on screen.
- Inspect accessible names/descriptions for all controls, unique identification where needed, and correct relationships between labels, hints, required status, and errors. A placeholder is not a replacement for a persistent label.
- For menus/dialogs/status updates, test focus entry/exit, background inertness where required, announcement of changes, and restoration after close. Dynamic content must not unexpectedly move focus or silently change the task.
- Test with at least one appropriate screen reader/browser combination when available, using a real task. Record exact combination, version if known, and what was or was not tested. A DOM or accessibility-tree inspection is not a screen-reader test.
- Include speech input/voice-control considerations for visible labels and accessible names when this is a key workflow. Test cognitive clarity: predictable navigation, descriptive instructions, low memory burden, visible confirmation, and error recovery.

## D. Forms and transactions

- Check labels, required fields, input purpose/autocomplete, format examples, constraints before submission, understandable errors tied to fields, preserved input after failure, and clear success confirmation.
- For multi-step or consequential actions, check review/correction/cancellation and whether timing/auto-advance could cause loss. Avoid relying on a particular visual position (“red field on the right”).
- Verify CAPTCHA, authentication, one-time codes, password managers, and re-entry do not block accessibility; record third-party responsibility and fallback where outside scope.
- If testing production, never submit real customer information or trigger actual contact, booking, or payment unless explicitly authorized. Use non-mutating traversal and mark final-submit behavior untested.

## E. Motion, touch, and responsive interaction

- Test `prefers-reduced-motion`; non-essential parallax, auto-rotation, smooth scrolling, and animation should not block use or induce motion. Check pause/stop/hide for moving content where relevant.
- Verify pointer targets against WCAG 2.2 AA Target Size (Minimum): generally 24×24 CSS px or permitted spacing/equivalent exceptions. Larger targets, often around 44×44, are a usability aim, not a universal WCAG AA requirement.
- Check orientation, landscape, touch without hover, pinch zoom, gesture alternatives, and overlays above virtual keyboards. Ensure responsive rearrangement preserves reading/focus order and all controls.

## Evidence discipline

For each finding: state page/state, exact control/content, user task, reproduction steps, expected versus observed behavior, affected input/AT/viewport, criterion if confident, and a suggested testable fix. Distinguish a definite violation from a usability concern or an unverified suspicion. Automated scan findings must be manually confirmed; a clean scan does not cover keyboard, screen reader, focus behavior, content meaning, or every WCAG criterion. For major journeys, include actual users with disabilities when feasible; one participant never represents every disability or assistive-technology use pattern.
