---
name: prepare-project
description: Prepare a software product or technical project before implementation through visual end-to-end product and user-experience walkthroughs, pipeline explanations, justified architecture and technology choices, a detailed technical specification, a dependency-aware build plan, and focused learning. Use when the user wants to understand the whole project before building, turn an agreed solution into a technical plan, compare major implementation choices, or prepare a project kickoff. Do not expand a small bug fix or isolated coding task into a full planning exercise.
---

# Prepare Project

Turn an idea or agreed solution into a project the user can **understand, challenge, and confidently build**. Produce both a coherent mental model and an actionable engineering handoff. Optimize for useful understanding and reduced delivery risk, not document length, an impressive stack, or an exhaustive list of technologies.

## Working approach

- Start from the latest agreement. Separate the problem, product direction, and technology choices already settled from genuinely open decisions. Do not restart discovery merely to fill a template. Reopen a settled decision only when new evidence materially changes its feasibility or consequences; explain that evidence.
- Calibrate to the user's knowledge, learning goals, available time, team, budget, existing system, and desired depth. Learn these from available context first. Do not infer expertise from casual language, prescribe a familiar stack without fit, or assume a solo project must be a throwaway prototype.
- Default to a thorough, layered explanation when the user asks for the whole project. Lead with the understandable story, then provide the detailed specification and plan. For a tight deadline, shorten scope and detail deliberately while preserving critical security, correctness, and data-integrity decisions.
- Ask only questions that change scope, architecture, cost, authorization, or the next useful step. Group the highest-value questions rather than presenting a long intake form. Continue independent work under explicit assumptions. An assumption is not a user decision.
- Keep a compact record of **verified facts**, **user decisions**, **recommendations**, **assumptions**, and **unresolved questions**. Link significant facts to their source or inspected artifact. Identify unavailable evidence instead of pretending it was checked.
- Treat planning as planning. Reading authorized context and drafting the requested plan do not authorize implementing it, provisioning services, purchasing, changing live systems, or creating a project backlog in another app. Follow the user's actual authorization and destination preferences. Do not invent extra approval gates if implementation is already explicitly authorized.

## 1. Establish the project frame

Create a short project brief: who it serves, what problem it solves, the user's intended outcome, the main workflow, success measures, constraints, and non-goals. Identify the first useful release and its difference from the longer-term vision.

For an existing project, inspect the actual relevant structure, contracts, dependency versions, deployment setup, tests, and prior decisions before proposing a replacement. Distinguish observed behavior from planned behavior. Reuse the system's strengths; do not prescribe a rewrite merely for stylistic preference.

Use [discovery-and-decisions.md](references/discovery-and-decisions.md) for uncertain requirements, architecture alternatives, research, or feasibility questions. Choose only the lenses that could affect this project.

## 2. Build the end-to-end mental model

Explain the product from the user's perspective before describing its infrastructure. Walk through a concrete, representative journey from entry to useful result, including relevant onboarding, configuration, repeated use, failure recovery, and exit or deletion.

For interactive products, read [experience-and-visualization.md](references/experience-and-visualization.md). Make the actual experience imaginable at every meaningful layer: information architecture, entry points, layouts, selection/input mechanisms, exact controls and actions, transitions, decisions, and system states. A list of pages or a sentence such as ‘select inputs and start review’ is not sufficient. Show how the user gets the inputs, distinguishes their roles, selects and validates them, triggers the action, sees progress, and reaches the next state. For API, command-line, or other nonvisual products, depict the equivalent consumer workflow rather than inventing a dashboard.

Use connected annotated wireframes, mockups, storyboards, or a lightweight prototype when layout or interaction is difficult to imagine, and whenever the user explicitly asks to visualize the workflow. Make a specific recommended layout, such as a table, card grid, or split view, and explain its fit instead of leaving it unspecified. Label recommendations and unresolved choices separately from confirmed decisions. Keep the visible flow consistent with actual scope and capabilities; a static mockup must not imply working functionality.

Then trace the corresponding request, data, or work item through the system:

1. What triggers it, and what input and identity it carries.
2. Where it goes, what each component is responsible for, and which boundary it crosses.
3. What is validated, transformed, persisted, scheduled, or sent to an external provider.
4. When the user sees success, what durable state proves success, and what may still be running.
5. What happens when an important dependency is slow, unavailable, duplicated, unauthorized, or partially successful.
6. How operators detect, investigate, and recover from the failure without losing or leaking data.

Follow one concrete example all the way through. Cover meaningful alternate journeys, not just the happy path. Include a component/flow diagram when the requested delivery surface supports it; otherwise use a numbered trace. Keep diagrams consistent with the prose. Omit components the project does not need rather than adding queues, caches, agents, or microservices by default.

Explain how the product is developed and shipped too: local development, checks, staging if needed, release, migrations, operations, and rollback. Clearly distinguish the runtime pipeline from the implementation workflow.

## 3. Make and explain consequential choices

Inventory the choices that determine feasibility, delivery effort, user experience, cost, risk, and future change. Consider build versus buy, architecture, interfaces, data and storage, hosting, integrations, authentication/authorization, background work, reliability, and any specialized technology actually needed.

For each consequential choice, explain:

- The problem the choice solves and the project-specific constraints it must meet.
- The recommended option and a small number of credible alternatives, including a simpler or existing approach when relevant.
- Why the recommendation fits these constraints better, what it gives up, and when an alternative would become better.
- Costs and failure modes, learning/operating burden, reversibility, migration implications, and evidence confidence.
- Whether the choice is confirmed, recommended, provisional pending a test, deferred, or needs the user's decision.

Do not invent historical rationale for a choice the user already made. Explain its present fit and tradeoffs, and label the analysis as such. Make recommendations instead of leaving the user with an undifferentiated menu. Avoid arbitrary numerical scores and presenting a low-confidence recommendation as settled.

Use targeted 80/20 research to resolve the few unknowns most likely to change the plan. Verify current provider behavior, limits, pricing, licenses, and versions when the recommendation depends on them. Prefer official documentation and primary evidence. Record what was actually checked, when, and what remains unverified. Stop when additional research is unlikely to change the next decision. Use a bounded feasibility spike only when permitted and when its result would materially change the approach.

## 4. Write the implementable specification

Use [spec-and-execution.md](references/spec-and-execution.md) to turn the mental model and choices into contracts, behavior, and verification criteria. Scale coverage to risk; do not dump every heading into every project.

Make enough explicit that a competent builder can start without silently making consequential product or architecture decisions. Include relevant UX states, component responsibilities, interfaces, data rules, permissions, integration behavior, failure recovery, performance expectations, security, observability, and testing. Separate first-release requirements from deferred capability.

Tie key requirements to observable acceptance criteria and planned tests. Call out missing access, unresolved contracts, unsupported assumptions, or feasibility questions that prevent an honest readiness claim. Do not disguise unresolved work as a precise schema, estimate, or confirmed integration.

## 5. Turn the specification into a build sequence

Plan from start to finish in demonstrable milestones. Begin with the highest-risk unknowns and the smallest useful end-to-end slice, then expand. Prefer vertical slices that prove an outcome over separate months of frontend, backend, and integration work with no usable flow.

For each milestone, state its outcome, dependencies, concrete work, test or demonstration, completion condition, and key risk. Include delivery, migration, release, and operational handoff, not just coding. Estimate with ranges and assumptions when useful; distinguish active effort from elapsed time and external waits. Do not invent a schedule without a capacity basis.

Identify what can run in parallel and which contracts must be settled first. Give the next executable step with its inputs and definition of done. Label optional later improvements and avoid treating an ambitious future architecture as a prerequisite for the first release.

For new application codebases, apply the installed `clean-codebase` skill to plan readable ownership and a replaceable frontend. Establish the client/backend contract before independent UI work so that separate contributors can work independently. Keep business rules and security authoritative outside presentation code, and include a short developer map and contract checks in the handoff.

## 6. Make understanding part of the deliverable

Use [learning-and-review.md](references/learning-and-review.md) when choosing explanations, a learning path, or the final readiness review.

For unfamiliar but consequential concepts, explain what it is, why this project needs it, how it works in this exact flow, and what happens if it is omitted or fails. Define terms before relying on them. Offer deeper explanations without burying the main story. Connect concepts into a causal model rather than producing a glossary of disconnected buzzwords.

Give an 80/20 learning sequence: the few concepts the user needs to evaluate and own the project now, the concepts best learned during implementation, and optional depth for later. Pair each immediate concept with a tiny concrete exercise or inspection that proves understanding. If the user is experienced, focus on unfamiliar domains and real tradeoffs instead of basic tutorials.

Use collaborative checkpoints for consequential choices and understanding, not a compulsory exam or repeated permission prompts. Preserve momentum if the user asks for one complete packet rather than an interactive workshop.

## 7. Review and hand off

Before declaring the plan ready, check consistency across product promises, visual experience and interaction contracts, pipeline, decisions, contracts, milestones, tests, cost assumptions, and operational responsibilities. Trace at least one main journey and one significant failure through the whole packet. Resolve contradictions or make the remaining blockers conspicuous.

Deliver, in the user's requested format:

- A short orientation: what will be built, how it works, the most important choices, and readiness status.
- The substantive project-preparation packet, including connected visual workflow artifacts when needed, with navigation for longer work and source links beside claims that depend on current evidence.
- The few decisions or missing inputs that actually need attention, the first concrete build step, and any conditions that must be met before implementation.

For long work, keep the chat summary short and provide the full requested artifact through the supported delivery tools. Do not substitute a summary for a requested detailed specification. Do not claim tests ran, integrations work, or implementation is complete merely because the plan describes them.
