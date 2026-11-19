---
name: brainstorm-to-backend
description: Turn a product brainstorming conversation into a self-contained backend build handoff, or receive that handoff and independently assess the starter system. Use when moving from brainstorming to a backend build chat, preserving user preferences while allowing architectural replacement and safe data evolution. Not a general-purpose backend implementation skill.
---

# Brainstorm to backend

Carry forward the user's intent, not loyalty to the starter architecture. This skill has two uses: prepare a backend build prompt in the brainstorming chat, or receive that prompt in the backend chat. Neither use alone authorizes implementation, data migration, cloud changes or deployment.

If the project has a standing engineering team, read its roster and current assignment first. This skill prepares or receives the backend owner's handoff; create-engineering-team owns explicit team creation or repair. Reuse the existing owner and follow its branch/review agreement. Carry the verified working directory, branch, assignment ID and dependency; do not create competing copies or assume chat titles isolate files. Consult applicable saved operating preferences and refresh stale version, provider and test claims before handoff.

## Prepare a handoff

1. Extract the product contract, user preferences, explicit decisions, rejected approaches and unresolved choices from the available conversation. Distinguish assistant recommendations from user requirements. Later user statements outrank older notes.
2. Inspect repository instructions, actual status, product and architecture documents, schema/migration inventory, server/domain entry points and Git state when accessible. Remain read-only. Do not assume a plan or a successful build means a feature is usable.
3. Separate **required behavior**, **current implementation**, **observed evidence**, **reported past evidence**, and **open work**. Current frameworks/providers may be reconsidered when permitted; safety properties and user-facing promises cannot simply disappear with a rewrite. Do not bake one project's stack, provider IDs or personal circumstances into this reusable skill.
4. Produce a self-contained prompt from the outline below, naming relevant paths and dated evidence. Exclude secrets, account tokens, private records and environment-file contents. Explain which settings must be obtained privately and whether local tools touch production. Do not transfer broad approval from an old task to a new operational action.
5. If preparing a frontend counterpart, use the same product facts and review checkpoint. Propose responsibility for shared interfaces and tests, rather than assigning both tasks unrestricted editing of the same files.
6. Create a task only on explicit request, using the app's project inventory and task tools when available. Use a separate worktree for a Git project unless the user requests direct use of the saved project. Do not invent a starting branch, provision services or copy secrets to make setup appear complete. If task creation is unavailable, provide the prompt and say so.

## What the backend prompt must carry

Write an actionable assignment, adapted to the actual project. Include:

- **Product purpose and scope:** audience, complete user journeys, supported interfaces, excluded features and real constraints. If the product is agent-friendly, state whether it supplies intelligence or exposes capabilities for user-provided agents; never infer a bundled AI product.
- **Starter-kit freedom:** inspect the entire system independently. Propose replacing data models, module boundaries, persistence adapters, API design, jobs, integrations or providers where justified. Follow repository instructions and raise conflicts. Architectural change needs evidence, compatibility and migration considerations; it is not a mandate to add distributed services or maximize abstraction.
- **Current baseline:** repo and documents, checked commit, deployed versus local behavior, known gaps and which evidence must be refreshed. Record provider/platform commitments as either user constraints or revisable choices.
- **Backend ownership:** authoritative domain rules, validation, accounts, authorization, persistence, APIs, agent access, imports/exports, background work, data lifecycle, operational visibility, resource limits and recovery.
- **Frontend boundary:** define usable requests, responses, pagination, errors and state transitions; frontend owns presentation and interaction. Shared actions must behave consistently across callers. Do not let separate adapters become conflicting business-rule implementations.
- **Contracts and coordination:** agree with the authorized counterpart on shared types, API shape, compatibility, common dependencies and cross-cutting tests before editing them. Name the exact workflow and observable behavior of each proposed change. Do not assume another task will silently adapt or merge your work.
- **Reliability and privacy:** evaluate separation between users, permission changes at execution time, duplicate requests, concurrent edits, time/units, import provenance, malformed inputs and data deletion as relevant to the product. Choose proportionate mechanisms, not speculative enterprise complexity. For existing users, migration and rollback must preserve their access and records.
- **Operational reality:** distinguish local simulations from real authentication/database tests; forecast free-tier limits using explicit assumptions, not invented user capacity; identify missing backup/restore, monitoring, retention and abuse controls. External actions need their own authority. Never treat free publication as legal or immigration clearance.
- **Acceptance:** verify full user journeys and negative cases, real integrations where authorized, manual/agent parity when required, migrations and recovery paths. Keep provider access, secrets, device work and user-only actions visible as specific blockers rather than faking success.
- **First action and stop point:** default to a read-only assessment when the user wants to evaluate first. State explicitly that no implementation, migrations, cloud settings, purchases, messages, pushes or deployments are authorized by that assessment request.

## Receive a handoff

Do not generate another prompt or spawn new chats. Read the supplied context and repository instructions, then independently inspect the system. Use relevant available architecture, framework, database, security and testing skills where needed; this skill is a handoff contract, not a replacement for domain guidance.

Inventory the source and trace representative commands from input through authentication, rules, storage and response. Assess tests against real failure modes, not their count. Read schemas and migration history before proposing a replacement. State what you did not inspect or test. Avoid running commands that modify production merely to strengthen a review.

For an assessment-first assignment, return:

1. A short plain-English account of what works, what is only planned, and what needs verification.
2. What to keep, change or replace, with specific evidence and tradeoffs.
3. The proposed architecture and ordered complete workflows, including data-preservation needs and integration with the frontend.
4. Required interface agreements, shared-file ownership, meaningful acceptance tests, operating gaps and only consequential questions.

Stop before implementation when instructed. Once approved, build and verify within the approved scope; preserve caller behavior or coordinate its replacement. Do not call deployed infrastructure, passing unit tests or synthetic integration results a finished product by themselves.

## Handoff quality check

Ensure a new chat can act without hidden context; product intent survived compression; stack preferences are not falsely immutable; rewrite freedom is real but data safety remains explicit; frontend boundaries are workable; past test reports are not fresh claims; no credentials leaked; and the next action matches permission. Do not create extra tasks to demonstrate the skill.
