# Depict the complete product experience

Use this reference to turn a feature list into an experience the user can actually picture, evaluate, and build. Cover each meaningful interaction layer, not merely a sequence of page names. Scale fidelity to the project; simplify the drawing before omitting a consequential step.

## Contents

- Start with the experience map
- Specify each surface and its layout
- Resolve entry, input, and selection paths
- Define action and transition contracts
- Depict states and recovery
- Produce connected visual artifacts
- Walk through a realistic scenario
- Review the experience against the system

## Start with the experience map

Ground the experience in the agreed product, actors, permissions, device, and first-release scope. Reconcile available user comments and existing designs before proposing changes. State what is confirmed, observed in an existing product, recommended, assumed, or unresolved. Do not turn a user's question about the layout into approval of a particular layout.

Map the information architecture: what the product's main objects are, how they relate, where the user finds them, and the navigation between them. Distinguish global navigation, an object's detail view, a task workspace, and temporary surfaces such as dialogs or drawers. A route is not necessarily a separate page; explain whether a transition replaces the workspace, updates a panel, or opens an overlay.

Show the complete relevant loop: first entry, setup or prerequisites, selecting/creating the thing to work on, performing the task, handling a decision, seeing the result, returning or repeating, and finding prior work later if history is in scope. Include alternate entry points such as a deep link, imported item, or empty account when they matter. Do not introduce login, history, sharing, or a dashboard merely to make the product seem complete.

For a command-line tool or API, map commands/requests, arguments, responses/events, terminal output or consumer-visible states, and recovery. Preserve the same level of interaction clarity without manufacturing a graphical interface.

## Specify each surface and its layout

For each important screen or workspace, describe:

- **Purpose and entry:** What the user is trying to do, how they arrive, and what context carries over.
- **Hierarchy:** Primary content, supporting context, navigation, and the most important action.
- **Structure:** Explicitly choose a table, card grid, list/detail view, split panes, canvas, wizard, form, or another justified arrangement. State where the regions are placed and what each displays. Avoid simply calling it a dashboard.
- **Content:** Actual proposed labels, representative values, columns or card fields, status indicators, help, and source/version identity where relevant. Use realistic synthetic content rather than rows of meaningless placeholders.
- **Controls:** Primary, secondary, and destructive actions; where they appear; what is visible or hidden; and what is enabled, disabled, or unavailable under which conditions.
- **Navigation and adaptation:** Back/cancel behavior, current location, whether selection survives navigation, and responsive or keyboard behavior relevant to supported devices.

Explain consequential layout tradeoffs. For example, a table helps compare many objects across consistent fields; a card grid emphasizes visual identity; a split workspace helps inspect two related objects without losing context. Recommend the fit for this project instead of leaving the user to choose from every layout pattern.

Represent distinctions with labels and structure, not color alone. Keep controls keyboard reachable and state changes perceivable. Do not add irrelevant mobile, localization, or visual-polish work when the product's scope does not require it.

## Resolve entry, input, and selection paths

Unpack phrases such as “pick a project,” “select old and new,” “upload a file,” or “start review.” These phrases often hide the most consequential product decisions.

State where available items come from: existing saved objects, an approved demo pair, local files, a repository, an external integration, a manual form, or another supported source. Show what happens before any item exists. Define which source methods are in scope; do not invent uploads, account connections, or arbitrary code execution while drawing a picker.

Specify how the user finds and identifies an item: relevant list fields, names, dates, versions, branch/commit IDs, previews, search/filter/sort only where useful, and availability or compatibility information. Distinguish a familiar display name from a stable identity. State whether selection happens in place, in a drawer/dialog, on a separate setup step, or through another explicit control.

For paired or multi-input workflows, make roles and grouping unambiguous. Specify whether users select a predefined pair, fill separate labeled slots, choose a baseline and candidate from one list, or follow a guided selection process. Show how they inspect, change, clear, or swap a selection when that behavior is supported. Do not assume all these mechanisms are needed.

Explain validation before the action: required inputs, incompatible combinations, permissions, incomplete uploads, unavailable versions, or missing configuration. State the exact start-button label, when it becomes enabled, and how the user learns what is missing. Show a final selection summary when mistaken identity would materially affect the result. Bind long-running results to the selected input versions so a later selection change does not relabel old results.

## Define action and transition contracts

For each consequential action, connect:

1. **Starting state and control:** Where the user is, the visible label, and its enabled condition.
2. **User input:** What they type, choose, drag, confirm, or cancel; include sensible defaults and validation behavior.
3. **Effect:** The command/request, data or permission effect, and whether it starts background work.
4. **Immediate feedback:** What changes on screen before completion, including button state and retained context.
5. **Destination or resulting state:** What appears next, which layout region changes, and what the user can do there.
6. **Recovery and repetition:** What back, cancel, retry, refresh, duplicate activation, or reopening does when relevant.

Use a compact interaction table or annotated flow when it improves clarity. Do not repeat a full contract for every decorative control; cover all actions that affect data, interpretation, progression, or recovery. A prototype's clickable route is not a substitute for specifying its actual effect.

Make decision points concrete: the options shown, evidence available, proposed default if any, consequences, confirmation needs, ability to defer or undo, and what happens afterward. Distinguish model suggestions, human choices, and system-confirmed outcomes. Avoid declaring an irreversible or external action approved merely because a mockup includes a confirmation button.

## Depict states and recovery

For each core surface or flow, identify applicable states and show meaningful variants:

- Empty/no data and the first useful action.
- Nothing selected, partial selection, valid selection, and invalid/incompatible input.
- Loading, validating, uploading, queued, processing, or saving, with honest progress and cancellation behavior where supported.
- Success, partial success, and the exact result the user can trust as complete.
- Validation errors, missing access, unavailable dependencies, timeout, and terminal failure.
- Stale input/result, unsaved changes, refresh/reopen, retry, deletion, or other relevant lifecycle states.

Specify visible messages and recovery actions, where they appear, and which input or completed work survives. Distinguish “no matching results” from “nothing has been created” and an operation's failure from a legitimate empty outcome. Do not show fabricated percentages, working features, or successful results merely to make the mockup attractive.

A small state matrix plus a few annotated variants often communicates more than a large set of nearly identical screens. Every major state still needs a defined behavior even when not separately drawn.

## Produce connected visual artifacts

Choose the smallest artifact that makes the workflow inspectable:

- A navigation/flow map for destinations, branches, and loops.
- Annotated low-fidelity wireframes for layout, hierarchy, controls, and selection mechanics.
- A storyboard for a sequence of visible states using one realistic scenario.
- A lightweight clickable prototype when the interaction itself needs evaluation and the environment and authorization support creating it.

For an explicit visualization request, provide actual visual representation, not only a promise that wireframes could be made. Use supported image, document, diagram, or prototype tools and their applicable instructions. If a tool or delivery surface cannot support the desired representation, provide the best supported annotated alternative and disclose that limitation. Do not publish or change a live application just to demonstrate a proposed experience.

Connect the artifacts. Number screens/states or label transitions consistently; show which control leads where and what changes. Include both the first-entry/selection stage and the main workspace, not only a polished final dashboard. Depict critical failure, empty, loading, and decision states as variants or annotations. Keep technical architecture diagrams separate from user-flow visuals, with clear links between them.

Label fidelity and status: proposed wireframe, confirmed design, illustrative data, static mockup, simulated interaction, or working prototype. Do not let visual polish imply confirmed product decisions or implemented backend behavior. Inspect rendered artifacts for legibility, clipping, contradictory labels, missing transitions, and alignment with the specification before delivery.

## Walk through a realistic scenario

Carry the same realistic example through the experience, visuals, and technical pipeline. Narrate what the user sees and does, not just what the system intends:

- Where they begin and the visible state.
- What they select or enter, why the displayed information identifies the correct input, and how roles differ.
- The exact control used and its immediate feedback.
- The next screen/state and the information needed for the next decision.
- The resulting artifact or outcome and how they return, repeat, or recover.

Cover the normal journey and at least one consequential alternate/failure journey. Trace the user-visible transition to the actual system event and durable state. If the interface promises “saved,” identify what has actually persisted; if a comparison uses selected versions, show those identities beside the result.

Do not skip setup because the eventual action sounds obvious. “Click Start review” is incomplete if the user cannot tell how the review's inputs were chosen, whether it opens another page, or what appears while work runs.

## Review the experience against the system

Run a mental or prototype walkthrough from a fresh entry state. At every step ask: Where am I? What do I see? What can I do? Why is this control available? What happens next? How do I fix a mistake? Can I get back without losing important work?

Check that every consequential control maps to a specified capability, permission check, data state, and acceptance test. Check the reverse direction too: important backend states must have a truthful user-facing representation. Align vocabulary, input identities, visual states, contracts, decisions, and milestones across the packet.

Resolve missing steps rather than treating them as polish for implementation. Mark genuinely open design choices clearly with a recommendation and the consequence of each option. Keep confirmed decisions intact unless new evidence warrants revisiting them.
