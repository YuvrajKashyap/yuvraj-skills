---
name: brainstorm-to-frontend
description: Turn a product brainstorming conversation into a self-contained frontend build handoff, or receive that handoff and independently assess the starter app. Use when moving from brainstorming to a frontend build chat, preserving user preferences while allowing redesign and replacement of existing code. Not a general-purpose UI implementation skill.
---

# Brainstorm to frontend

Carry forward the user's intent, not loyalty to the starter implementation. This skill has two uses: prepare a frontend build prompt in the brainstorming chat, or receive that prompt in the frontend chat. Neither use alone authorizes product implementation or deployment.

If the project has a standing engineering team, read its roster and current assignment first. This skill prepares or receives the frontend owner's handoff; create-engineering-team owns explicit team creation or repair. Reuse the existing owner and follow its branch/review agreement. Carry the verified working directory, branch, assignment ID and dependency; do not create competing copies or assume chat titles isolate files. Consult applicable saved operating preferences and refresh stale version, provider and test claims before handoff.

## Prepare a handoff

1. Extract relevant user decisions from the available conversation. Separate explicit requirements, preferences, tentative ideas, rejected approaches, and unresolved choices. Later direct statements outrank older brainstorming. Do not turn every assistant suggestion into a requirement.
2. Inspect the repository's own instructions, current status, product specification, relevant UI entry points, and Git state when accessible. Do not change the app while preparing a handoff. Do not claim to have read every source file if you have only sampled entry points.
3. Carry only relevant context, not a transcript dump. Include exact project paths and verified task IDs when useful; never include credentials, session links, private health records, or environment-file contents. If a file is unavailable in the receiving environment, summarize the required facts rather than relying on a broken path.
4. Label shipped/tested facts with their evidence and date. Label inherited reports as reports, not fresh verification. Mark planned features and unknowns explicitly. Existing architecture and visual design are a baseline, not automatic constraints; distinguish them from actual user requirements and repository instructions.
5. Produce a self-contained frontend prompt using the content outline below. If the user also asks for a backend handoff, agree on the same product facts, review checkpoint, and proposed interface boundary across both. Neither task is implicitly authorized to merge or deploy the other's work.
6. Create a task only when explicitly requested. Use the application's project inventory and task-creation tools when available. For a Git project, use a separate worktree by default unless the user asks for the saved project directly. Never invent a branch or copy private environment files into it. Report setup prerequisites honestly. If creation is unavailable, deliver the copy-ready prompt instead of pretending a task exists.

## What the frontend prompt must carry

Write a direct assignment, not an abstract checklist. Adapt its length to the actual context. It must establish:

- **Mission and scope:** the product's audience, purpose, core workflows, current platforms, what is excluded, and the frontend's ownership of the complete user experience.
- **Starter-kit freedom:** independently assess the whole implementation; freely propose replacing navigation, layout, visual language, components, client state, and interaction patterns. Follow repository instructions; flag conflicts instead of silently overriding them. A major stack change needs a reason and a coordination plan, not permission inferred from "rewrite anything."
- **Preferences and taste:** carry the user's actual design references and feedback, if any. Do not invent a preferred visual style. Evaluate existing branding rather than treating it as sacred.
- **Current baseline:** workspace, relevant documents, current commit if checked, what's implemented versus verified, known gaps, and any live-user or shared-environment risks.
- **Frontend ownership:** journeys, page structure, forms, onboarding/account screens, mobile and desktop behavior, accessibility, visual states, perceived speed, client-side drafts, and integration with actual backend behavior.
- **Backend boundary:** backend owns authoritative validation, permissions, calculations and saved-data behavior. Propose needed inputs, responses, errors and state transitions; do not duplicate business rules in UI or invent a successful response for missing functionality. Temporary fixtures must be clearly identified and never presented as shipped integration.
- **Shared change agreement:** identify who owns shared types, API contracts, dependencies, route boundaries, and cross-cutting tests before editing them. A directory split alone is not sufficient. For each proposed contract change, name the affected workflow, request/response examples, errors, compatibility needs, and owner. Share only with the specifically authorized counterpart task.
- **Quality evidence:** test real journeys and their empty, loading, success, error, offline and conflict states where relevant; inspect phone/desktop screenshots; verify keyboard, screen-reader semantics and reduced motion; measure meaningful interaction speed. Compilation alone is not acceptance. Do not equate browser emulation with physical-device testing.
- **First action and stop point:** unless implementation is explicitly authorized now, perform a read-only assessment and stop with a proposed direction. Do not treat historical "build everything" requests as overriding the current review-first checkpoint.

## Receive a handoff

Do not generate another handoff or create more chats. Read the supplied product context and repository instructions, then independently assess the frontend. Use relevant available design, framework, accessibility and testing skills as the work warrants; this handoff skill does not substitute for them.

Review representative end-to-end journeys, component/state boundaries and the actual rendered app when a safe local preview is available. Inspect the complete source inventory and trace important flows; state any areas not examined. Existing screenshots, tests and prior agents' claims are evidence to evaluate, not proof to repeat blindly. Do not start a server that connects to live services without checking configuration and the task's authority. Use synthetic fixtures.

For an assessment-first assignment, return:

1. A short plain-English account of what a user can do today and what remains unverified.
2. What to keep, change or replace, with specific code/experience evidence and reasons.
3. The proposed experience and the order of complete user journeys to build. Keep the full-product destination visible.
4. Required backend agreements, shared-file ownership, verification criteria, and only the questions that materially affect direction.

Stop before implementation when instructed. After approval, retain the same ownership and safety boundaries throughout iteration. Clearly distinguish local work, integrated work and published work.

## Handoff quality check

Before delivery, check that a fresh chat can understand the assignment without the original conversation; facts and proposals are separated; "starter kit" means genuine design freedom; no product requirements disappeared; backend dependencies are explicit; private settings were not copied; and the first action matches current permission. Never create extra tasks just to demonstrate the skill.
