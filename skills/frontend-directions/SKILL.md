---
name: frontend-directions
description: Build several complete, switchable frontends for the same product. Use when exploring alternative visual directions, comparing redesigns, or combining the strongest parts of several designs.
---

# Frontend directions

Give the user real alternatives they can walk through. Default to five directions when the brief leaves the count open. Each should be good enough to ship on its own. Give each the ambition of a flagship frontend, from type and composition to cinematic motion and responsive interactions. If available, max-frontend can supply additional inspiration.

Read the brief and walk the existing experience. Identify the audiences, essential journeys, brand commitments, content, and backend contracts each direction must carry. Keep claims factual. Ask about the primary audience or action if it would materially change the concepts.

Sketch more ideas than needed. Choose directions that differ in structure, medium, and interaction. Give each a one-line premise, a reason it fits this particular product, and a moment a visitor would remember. A field guide, a live instrument, and an exploded object suggest different ways to navigate or understand a subject. Invent stronger ideas whenever the brief suggests them.

Preserve the current frontend as a selectable baseline. Register each direction under a stable name, keep its presentation isolated, and share the content and business operations. Give the reviewer a picker and direct preview links. Keep existing deep links working. See the [switching guide](references/switching.md).

Build each direction from a blank presentation layer. Carry the idea through the full journey, including the main action, loading, failure, and confirmation. Give touch, keyboard, and reduced-motion users a complete experience. A single agent can build each direction in sequence. If the environment supports authorized parallel work, assign one folder per builder and coordinate shared changes centrally. Use the [builder brief](references/builder-brief.md) in either mode.

Open every preview at desktop and narrow phone widths. Walk its primary action with isolated test data, verify the actual result, and check navigation, focus, overflow, console errors, and the production build. Compare each direction with the baseline. Identify the weakest moment in each and improve it before presenting the set. If a preview appears sluggish, compare it with a simple page in the same environment before attributing the problem to the design.

Hand over the picker URL, each direction's premise and preview link, the checks performed, and how to restore the baseline. Let the user choose. If they want a combination, build it as a new registered direction, keeping the alternatives accessible until the user explicitly approves their removal.
