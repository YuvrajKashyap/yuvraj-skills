# Discovery, research, and consequential decisions

Use this reference when project definition or technical choices need work. It is a menu of useful checks, not a mandatory questionnaire.

## Project brief

Capture the smallest set of facts that changes the engineering plan:

- **Problem and user:** Who experiences the problem, when, how they solve it now, and why a change is valuable.
- **Outcome:** What a successful use looks like. Separate business or user outcomes from technical performance and project-delivery goals.
- **Product boundary:** Core journeys, first-release must-haves, explicit non-goals, external actors, and what remains manual.
- **Constraints:** Deadline, budget, actual team/capacity, existing skills, supported devices, deployment environment, data sensitivity, accessibility, integration access, relevant jurisdiction or domain obligations.
- **Ownership:** Who maintains, pays for, deploys, supports, and makes consequential product decisions. Mark unknown ownership rather than assigning people without evidence.
- **Success criteria:** Observable outcome, measure or test, proposed target, and where evidence will come from. Label targets as proposed until confirmed; do not fabricate a baseline.

Distinguish deadlines from aspirations and hard requirements from preferences. If two goals conflict, make the conflict explicit and recommend a tradeoff. For example, rapid delivery and a wholly self-hosted stack may require narrowing scope or increasing operating effort.

## Work with an existing system

Inventory only the relevant evidence: architecture docs, source boundaries, dependency manifest and lockfile, API contracts, database definitions and migrations, authentication model, CI/deployment configuration, tests, issues, and observed failures. Do not inspect secret values to learn whether a service is configured.

Classify components as retain, extend, replace, or investigate, with a reason. Identify compatibility and migration requirements before proposing a replacement. Keep a proposed future design separate from the current implementation. If repository access is unavailable, provide a provisional design and name the inspection that would confirm it.

## Decision inventory

Choose categories based on the project. Do not create artificial decisions just to discuss technologies.

- **Product and interaction:** Web/mobile/desktop/API, online/offline behavior, single- or multi-user, roles and account model, automation versus human control, build/buy/manual alternatives.
- **Execution architecture:** Single application or service boundaries, client/server responsibility, synchronous/asynchronous work, batch versus streaming, long-running workflows, locality and trust boundaries.
- **Implementation stack:** Language/runtime, framework, supported versions, ecosystem fit, testability, deployment compatibility, team's learning cost and ownership.
- **Data:** System of record, relational/document/object storage, consistency, transaction boundaries, search, cache need, data portability and lifecycle.
- **Identity and access:** Managed or existing identity, authorization model, tenancy/isolation, session handling, service-to-service identity.
- **External services:** Provider capability and limits, official API availability, terms/license implications, billing unit, data handling, support, outage fallback and exit path.
- **Delivery and operations:** Hosting model, deployment simplicity, environments, migrations, observability, backups/recovery, operating cost and responsibility.
- **Specialized methods:** AI versus deterministic logic, model/tool choices, indexing/retrieval, algorithms, evaluation, hardware, or scientific methods only when they drive the product.

For a small app, many choices can be one coherent architecture recommendation with brief supporting decisions. For expensive, hard-to-reverse, or security-sensitive choices, create a fuller decision record.

## Decision record

Use this structure when it earns its detail:

1. **Decision and status:** A precise statement; confirmed, recommended, provisional, deferred, or awaiting user input.
2. **Context:** Requirement and constraints, including anything fixed by the user.
3. **Viable options:** Usually the recommended approach plus one or two credible alternatives. Include keeping the current solution or doing less when reasonable.
4. **Criteria:** Compare on the few dimensions that matter here. Examples: correct behavior, delivery time, maintainability, security, operating burden, recurring cost, portability, offline support, or learning value.
5. **Recommendation and rationale:** Explain how the constraints lead to the choice. Separate evidence from judgment.
6. **Accepted downside:** What becomes worse or remains unsolved, who bears the burden, and a mitigation if justified.
7. **Revisit condition:** A measured threshold, changed constraint, failed experiment, provider issue, or other concrete trigger; not vague future scale.
8. **Validation and confidence:** Evidence/date, unanswered question, bounded test, and whether uncertainty blocks the next milestone.

Avoid fake precision. If scoring helps, explain weights and acknowledge that the numbers express judgment rather than measured truth. If a preference is subjective, name it honestly.

## 80/20 research loop

1. List uncertainties with consequence if wrong, likelihood, cost to resolve, and the decision they affect.
2. Research the highest-leverage uncertainty first. Write the question before searching, such as whether the chosen host can execute the required maximum-duration job.
3. Check authoritative current sources for version-specific behavior, APIs, limits, provider pricing, license or data-use conditions. Use practitioner experience to reveal caveats, not to overrule authoritative facts without explanation.
4. Keep a small evidence ledger: question, source/link, date or version, finding, decision consequence, and confidence. Record conflicts or unavailable information.
5. Translate the finding into a recommendation or a bounded experiment. Stop when the remaining uncertainty cannot change the next safe step or requires the user's input.

Timebox research proportionally to project stakes and deadline. Do not claim “80/20” means exactly 20% effort or use it to skip fundamentals. If browsing is unavailable, state which claims are provisional and what must be verified later. Do not present general knowledge as newly researched evidence.

## Feasibility spikes

Use a spike only if a small experiment can resolve a major unknown more cheaply than speculative design. Describe the question, permitted environment, minimal setup, synthetic/sanitized data, time/cost cap, observable pass/fail condition, and how either outcome changes the plan. Obtain any required authorization for execution or external effects. A proposed spike is not a completed test.

Examples include validating an API's required capability, proving a target device can meet an actual latency budget, or testing an import on representative synthetic data. Avoid building half the product under the label of research.

## Cost and scale without speculation

State a baseline scenario with explicit workload assumptions: users, active sessions, requests/jobs, storage, transfer, paid API calls, or model tokens as applicable. Explain the cost model, free-tier assumptions, one-time costs, and largest scaling drivers. Cite current prices only when verified and show uncertainty as ranges.

Prefer the simplest architecture that meets stated needs. Avoid speculative capacity claims. State what to measure after launch and the threshold that would justify adding a cache, queue, specialized datastore, service split, or other complexity. Explain why a critical component is necessary now when deferring it would be unsafe or architecturally misleading.
