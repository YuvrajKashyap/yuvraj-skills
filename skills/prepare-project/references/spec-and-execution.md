# Technical specification and execution plan

Use this reference when drafting the full preparation packet. Adapt the depth to the project and retain only relevant sections. Explain any consequential omission or unresolved dependency rather than filling pages with boilerplate.

## Contents

- A readable packet
- Product behavior
- System boundaries and runtime flow
- Data and interfaces
- Quality and safety requirements
- Development and delivery
- Milestones that demonstrate progress
- Traceability and risks
- Handoff and definition of ready

## A readable packet

For a substantial project, organize the artifact into:

1. Project brief, success, scope, and non-goals.
2. Product experience map, connected screen/interaction walkthrough, and system/pipeline walkthrough.
3. Architecture and consequential decision records.
4. Behavioral and technical specification.
5. Implementation milestones and verification plan.
6. Learning path, risks, open decisions, and readiness summary.

Use navigation for long work. Give the user the coherent story first, then the contracts that builders need. Keep a single canonical definition for each requirement and link rather than copying contradictions across sections. For a small project, merge sections while preserving the substance.

## Product behavior

Describe each core journey in terms of actor, intent, preconditions, main steps, outcome, state changes, and meaningful alternatives. Specify applicable empty, loading, success, partial-success, error, permission-denied, offline, cancellation, and recovery states.

Use the experience reference linked from SKILL.md to specify visible surfaces, layout and navigation, input/selection paths, control labels, enabled/disabled conditions, transitions, and preserved state. Link each consequential UI action to its data/API effects and acceptance criteria. Mockups and the technical contracts must describe the same behavior; a proposed control cannot promise an unsupported capability.

Call out user trust concerns: what happens automatically, what requires review, whether actions can be undone, whether status reflects durable completion, and what information is exposed to whom. Include accessibility, supported devices, keyboard/screen-reader behavior, or localization when relevant to the product's users. Do not invent detailed visuals if the user only requested backend planning.

## System boundaries and runtime flow

Identify each component's responsibility, inputs/outputs, owned state, and connections. Separate user devices, trusted backend, storage, background workers, and external providers. Mark trust boundaries and where permissions are enforced. Avoid duplicate ownership of critical data.

Trace at least one real-shaped example through the intended design. Identify:

- Request or event source and validation.
- Authentication and authorization before access or effects.
- Internal transformations and business rules.
- External calls, persistence, transaction or consistency boundaries.
- Synchronous response versus eventual work and user-visible status.
- Failures, retries, deduplication/idempotency, compensation or recovery where needed.
- Logs/metrics/traces and safe support diagnostics.

Use a state machine when transitions or partial completion are a source of bugs. Make cancellation, retry, and timeout behavior precise for workflows that need them. Do not add distributed-system machinery to a simple synchronous operation without a real reason.

## Data and interfaces

Specify relevant entities, relationships, identifiers, ownership, uniqueness/invariants, lifecycle, and validation rules. State how dates/time zones, money/currency, concurrency, or ordering are handled when applicable. Separate source-of-truth records from caches, projections, and derived outputs.

For public or inter-component contracts, provide the minimum implementable detail:

- Operation or event name and purpose.
- Caller, authorization, required input, and response or event shape.
- Validation and versioning assumptions.
- Side effects and success semantics.
- Errors, rate/size limits, pagination, timeouts, and idempotency where relevant.

Keep illustrative payloads labeled as proposed; use synthetic data. Specify migrations and backward compatibility when existing users or data are affected. Include retention, export, deletion, and backup/restore expectations where appropriate. Do not turn an unverified provider API into an asserted contract.

## Quality and safety requirements

Select measurable targets appropriate to stakes and workload. Mark proposed targets and state how they will be measured. Cover the relevant subset of:

- Correctness, consistency, integrity, availability, latency, throughput, and resource use.
- Authentication, least-privilege authorization, tenant/user isolation, secure secret handling, input validation, and abuse/rate controls.
- Sensitive data collection/transmission/storage, retention, logging redaction, and provider data use. Identify specialized compliance review needs without declaring compliance.
- Dependency/supply-chain risk, backups, restore tests, migration safety, auditability, and recovery procedures.
- Accessibility, responsive behavior, browser/device support, and degraded/offline behavior.

For AI-enabled features, separate deterministic responsibilities from model judgment. Specify evaluation examples, success/failure criteria, uncertainty display, prompt-injection boundaries, untrusted inputs, tool permissions, data handling, model/provider limits, cost/latency budgets, fallback and human review where needed. Do not assume a prompt alone guarantees correctness or authorization.

## Development and delivery

Describe local setup and environment needs without including secrets. Name required services and configuration categories; document exact versions or commands only when verified or explicitly proposed. Outline a navigable module layout if useful, labeling it as proposed until it matches the actual repository.

Specify the quality checks that gate delivery: unit/domain tests, integration/contract tests, representative end-to-end journeys, failure tests, accessibility, security, performance, or evaluation suites as warranted. Connect tests to product requirements rather than promising coverage percentages without meaning.

Include build/deploy ownership, environments, automated checks, migration order, health checks, release strategy, rollback or forward-recovery constraints, monitoring, and post-launch validation. Explain when a database or external side effect cannot be reversed by simply redeploying older code.

## Milestones that demonstrate progress

Choose a sequence for this project, not a universal ceremony. A common useful progression is:

- Resolve the highest-risk unknown or obtain required access.
- Establish the minimal development/testing foundation.
- Complete one thin end-to-end journey with realistic boundaries.
- Expand essential workflows and product states.
- Harden correctness, permissions, failure handling, usability, and operations.
- Release safely, verify the production outcome, and hand over maintenance.

Each milestone should contain:

- **Outcome:** What can be demonstrated to the user afterward.
- **Work:** Concrete implementation tasks sized so a builder can start without rediscovering the design.
- **Dependencies:** Required decisions, interfaces, access, earlier work, or external input.
- **Verification:** Specific tests or evidence and the acceptance threshold.
- **Completion condition:** What makes it done, including important non-code work.
- **Risk and fallback:** The main uncertainty and what happens if the approach fails.
- **Effort:** A range if useful, its assumptions, and external wait time separately. Avoid calendar commitments without real capacity.

Mark independent work that can proceed in parallel. Keep ownership recommendations distinct from confirmed assignments. Preserve the user's chosen issue tracker or document destination, but creating tasks in it requires the applicable authorization.

## Traceability and risks

Maintain lightweight links: important goal → journey/requirement → component or decision → milestone → acceptance test. Use IDs only when they improve navigation. A small project may use plain names rather than a requirements bureaucracy.

Record major risks with cause, user/project impact, likelihood or confidence, mitigation, early warning/validation, and the point at which work must stop or change course. Put unresolved high-impact assumptions near the plan's beginning rather than hiding them in an appendix.

## Handoff and definition of ready

Identify the first executable task with inputs, output, checks, and a stopping condition. Include enough context that a builder can act without inventing scope. Give explicit boundaries on what not to build yet.

Use a candid status:

- **Ready for the next implementation step:** Scope, relevant contracts, and major decisions are sufficient for that step; remaining work is deliberately deferred.
- **Ready with conditions:** Useful independent work can start, but named assumptions, access, or decisions gate specified later work.
- **Not ready:** A missing requirement, unsafe assumption, infeasible dependency, or unresolved high-impact decision blocks the next meaningful step.

Readiness is relative to the next safe increment, not a claim that every future detail is known. Do not require exhaustive up-front design before learning from implementation.
