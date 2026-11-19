# Learning, interaction, and readiness review

Use this reference to make a technically detailed packet understandable and to check that it is useful rather than merely comprehensive.

## Explain in layers

Start with what the product does for its user. Then explain the major pieces, then the concrete flow between them, then the decisions and implementation details. Let the reader understand the purpose of a component before introducing its API or framework.

For an unfamiliar consequential concept, use:

1. **Plain-language idea:** A concise definition without unexplained jargon.
2. **Role in this project:** The exact problem it solves and where it appears in the flow.
3. **Concrete example:** Use the same representative request or data item as the system walkthrough.
4. **Mechanism and constraint:** Enough fundamentals to reason about its behavior, not just operate a tool.
5. **Tradeoff or failure:** What can go wrong, what the design gives up, and when another approach would fit.

Use analogies only when they clarify; identify the point where the analogy stops being accurate. Explain acronyms on first use. Do not oversimplify “eventually consistent” into “always up to date” or treat authentication as permission to access every record.

Explain the connection between decisions. For example, background processing changes status UX, retry semantics, idempotency, persistence, observability, deployment, and cost. A list of tool descriptions is not an end-to-end understanding.

## An 80/20 learning path

Calibrate to what the user already knows and wants to own. Prioritize concepts that unlock several project decisions or prevent costly mistakes.

For each immediate learning item, give:

- The concept and why it matters here.
- What the user should be able to explain or do afterward.
- A tiny exercise, diagram, inspection, or worked example using this project.
- An authoritative learning source if needed and actually verified.
- What can safely wait until implementation or later scale.

Separate **understand before building**, **learn while building**, and **optional later depth**. Do not prescribe a long course as a prerequisite to a small project. A focused local example or walkthrough often teaches more than a reading list. Do not give arbitrary time promises; state estimated learning time as an assumption if it helps scheduling.

## Interaction without stalling

Choose interaction depth from the user's request:

- **Complete packet:** Make reasonable labeled assumptions, deliver a coherent draft, and collect consequential questions together. Do not withhold the useful result pending a survey.
- **Guided workshop:** Work through brief, journey, pipeline, choices, and plan in manageable stages. Ask the user to choose or explain only when it helps the next step.
- **Deadline-constrained preparation:** Cover scope, main flow, critical choices, highest risks, and next build step first. Mark deferred detail and what cannot safely be skipped.

A checkpoint should make a decision easier, such as “This provider reduces setup but stores uploads outside our infrastructure. Here is the verified data handling and the alternative.” Do not ask vague “Does this make sense?” after every paragraph. Offer a quick teach-back or scenario question when the user wants learning support, but do not make it an exam.

Do not interpret silence as approval of a consequential choice. Continue independent planning under a labeled recommendation when possible. End with a small number of questions that genuinely need the user, not every unknown.

## Consistency review

Read the packet as both the user and the builder. Check:

- **Understanding:** Could the user describe what happens from initial action to durable outcome, what the main components do, and why they exist?
- **Product integrity:** Are first-release promises, non-goals, journeys, and acceptance criteria consistent? Does the plan build the agreed solution?
- **Experience completeness:** Can the user mentally or visually walk from the first entry point through exact input choices, controls, layouts, transitions, and results without inventing missing steps? Are meaningful states and recovery paths depicted, and do the visuals match the specified capabilities? Are recommended designs clearly distinct from confirmed decisions?
- **Architecture integrity:** Does every important flow have an owner and a complete path? Are contracts, state transitions, data ownership, and permission checks consistent?
- **Decision quality:** Are major choices justified against actual constraints, with credible alternatives, accepted downsides, evidence confidence, and revisit conditions?
- **Failure handling:** Does at least one significant failure trace work end to end? Can partial completion, retry, duplicate work, access denial, or dependency outage produce unsafe state?
- **Delivery integrity:** Do milestones build the required components before they are used? Are critical dependencies, tests, release steps, and operational responsibilities covered?
- **Evidence integrity:** Are observed facts, proposed designs, user decisions, assumptions, and unchecked claims clearly distinguished? Are current source-dependent claims sourced?
- **Proportionality:** Is any component, process, research branch, or learning task more complex than the project's needs justify? Does simplification preserve safety and quality?
- **Actionability:** Can the builder start the next authorized task with clear inputs and completion criteria? Can the user see what still needs a decision?

Fix contradictions before polishing prose. Name unresolved issues precisely: the affected decision, evidence missing, consequence, owner if known, and next check. Do not hide an important unknown behind a large polished document.
