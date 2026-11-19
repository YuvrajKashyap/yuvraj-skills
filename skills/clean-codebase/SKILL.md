---
name: clean-codebase
description: Audit, organize, simplify, and improve a codebase for long-term ownership. Use when the user asks for clean readable code, clear architecture, easy navigation, maintainability, repo cleanup, or measured efficiency. Also apply the relevant checks while implementing changes in repositories that explicitly adopt this standard. Preserve product behavior and avoid speculative abstractions.
---

# Clean Codebase: clear to read, obvious to navigate, efficient to run

## Long-term ownership

This is a serious ownership standard, not a cosmetic cleanup request. Aim for a codebase that maintainers can keep for years, grow substantially, understand again after months away, and hand to another person, Claude, Codex, or another capable agent without a private explanation of how everything works.

**CLEAN. READABLE. EASY TO FOLLOW. EASY TO NAVIGATE. SIMPLE TO EXTEND. FAST WHERE IT MATTERS.**

No messy source code. No random files scattered around. No folders whose purpose nobody can explain. No clever abstractions that make a simple change require a tour of the whole repository. No claims of amazing performance without evidence. No rushed scaffolding presented as a finished foundation.

Treat the user's strongest words as a quality bar, not permission to rewrite everything. Go deep on understanding, verification, and removal of actual friction. Do not go deep on unnecessary architecture. The goal is excellent engineering with less confusion, less wasted work, fewer hidden assumptions, and a shorter path from intention to a correct change.

**Make it neat. Make it navigable. Make it readable. Make it efficient. Then prove those improvements in the actual repository.**

## Preserve scope and ownership

- Read repository instructions and the current tree before proposing a structure. The repository's domain and current user request determine what belongs together.
- Inspect Git status before editing. Preserve unrelated work, public interfaces, and intentional designs. Do not reset, clean, mass-delete, or overwrite another person's changes.
- Improve authorized local work autonomously. A request to clean a repo does not authorize deployment, publication, contacting people, paid services, or unrelated machine changes.
- Do not turn this skill into mandatory bureaucracy for a tiny fix. Apply the relevant checks at the scale of the task. A spelling fix does not need an architecture review.
- Do not force this repository's stack, folder names, exact numeric limits, or framework onto other projects.

## First understand the story

Trace one real user flow from its entry point through its data, state, rendering, persistence, and failure behavior. Then trace one real contributor flow from opening the README to adding, running, testing, and reviewing a change.

Answer these in ordinary language:

1. What does the product do, and what is outside its scope?
2. Where does someone start reading? Where does the application start running?
3. Which folder owns each capability? Which data is authoritative? Which outputs are generated?
4. What does a normal change require, and why does it touch those files?
5. How does the contributor know the change works? What checks enforce that?
6. What happens when the collection, dataset, traffic, or number of contributors grows?

If these answers require tribal knowledge, fix the code organization, names, or documentation that hides them. Do not merely write a long document explaining a confusing implementation that could be simplified.

## Organize by responsibility; order by meaning

Keep one obvious owner for each behavior. Co-locate code that changes together. Separate application code, individual features or projects, automation, generated output, and documentation when they are genuinely different responsibilities.

Use descriptive names. Prefer a short path that explains itself to a deep directory hierarchy. A folder should tell the next person why its contents belong together. Avoid dumping grounds such as enormous `utils`, `misc`, `helpers`, or `common` folders. Extract a shared module when there are actual shared callers and a stable concept, not just two similar-looking lines.

**Chronological means chronological where time is the concept.** Use explicit validated dates for timelines, release history, migrations, and project collections. Use stable identifiers or sequence numbers when identity must survive reordering. Use a generated index or navigation page when folders need a readable chronological view. Do not rename every source file with a number: source code should follow responsibility and execution flow. Do not silently guess missing historical dates; verify them from evidence or mark them unknown.

Within a source file, present a clear path: imports, relevant types/constants, the main exported behavior, then focused implementation helpers as appropriate to local conventions. Keep related logic together. Avoid forcing a rigid file-order rule when it makes the framework's entry point harder to see.

**Easy to navigate means easy to navigate.** A reader should be able to follow imports, filenames, links, and ownership notes without guessing. Check that links resolve. Update callers and documentation when moving things. Do not leave two competing sources of truth after a refactor.

## Make the repository obvious in the editor

Consider explicit `frontend/` and `backend/` boundaries for full-stack applications. The exact names are a preference; recognizable ownership, protected trust boundaries, and easy navigation are engineering requirements. Put trusted execution, providers, and authoritative persistence under the backend boundary, with shared contracts and browser integration clearly named separately. For an existing repository, preserve working behavior and update imports, scripts, tooling, documentation, and deferred checks together when relocating code. Never mistake a folder rename for proof of architectural isolation.

Use the fewest files that keep responsibilities understandable. Keep closely related code together; do not create a file per tiny helper, duplicate facade, empty layer, or framework-shaped folder without a concrete need. Split a large file when it mixes responsibilities or makes navigation harder, not to meet an arbitrary line count. Prefer short, descriptive, consistent domain names and shallow feature/responsibility groups. Order declarations in a readable progression and provide a short reading order for important flows. Avoid decorative numeric prefixes where alphabetical or domain grouping is clearer.

Make handwritten code teach its structure: add a concise purpose/boundary comment to nontrivial modules, document exported operations and important inputs/outputs, and explain state transitions, approval snapshots, error handling, and non-obvious decisions at their implementation sites. Keep them specific and maintained with the code; do not narrate every obvious assignment, fill JSX with redundant prose, or edit generated/vendor code to add comments. Comments complement clear names and small interfaces rather than compensating for confusing structure.

Write comments in simple, everyday language so a newcomer can follow what is happening. Explain technical terms when they are needed; prefer "saved copy of the reviewed proposal" over unexplained jargon such as "immutable revision-bound snapshot." Add enough comments throughout meaningful steps, branches and failure paths to explain what happens and why, not just a header at the top of the file. Do not comment every obvious line. Read comments as a beginner would and simplify dense wording before handing off. Keep precise identifiers where they help someone find the actual code.

Keep generated output, dependencies, local runtime files and caches distinguishable from source. When editor clutter impairs navigation, add repository-scoped Explorer exclusions for those artifacts without deleting data or hiding authored source, instructions, or configuration. Keep a concise root directory map and link to the real entrypoints. A new contributor should locate UI, backend behavior, shared contracts, fixtures and tooling directly from the tree.

## Readable implementation is the default

- Use names that explain intent, inputs, and outputs. Avoid abbreviations that save typing at the expense of comprehension.
- Replace compressed one-line logic, nested ternaries, and mixed concerns with straightforward code when doing so improves reading.
- Prefer explicit control flow and small interfaces. A good module hides implementation detail without hiding essential behavior.
- Avoid unnecessary factories, registries, event buses, adapters, wrapper hooks, dependency-injection frameworks, or generic engines. Use them only where the product already has meaningful variation or a demonstrated need.
- Validate inputs at real entry points. Make failures actionable and identify the file, operation, or input that caused them. Do not swallow errors indiscriminately.
- Delete confirmed dead internal code. Before deleting exports, dependencies, files, or scripts, check dynamic imports, framework conventions, tooling entry points, external/public consumers, and compatibility expectations.
- Keep comments for intent, invariants, and non-obvious tradeoffs. Do not narrate obvious syntax. Do not replace clear code with essays.
- Establish one formatter and a compatible lint setup. Enforce consistency mechanically rather than depending on every model remembering a style preference.

**Readable is not verbose. Simple is not careless. Compact is not automatically clean.** The reader should understand what happens and why without mentally executing a puzzle.

## Efficiency must be real

Start from an observed cost, a reproducible failure, or a clearly bounded resource problem. Record what is slow, when it is slow, the dataset/device/build mode, and how it will be measured.

Inspect the applicable areas:

- Work loaded before the user needs it: JavaScript, images, fonts, full previews, heavy libraries, eager imports, route prefetching.
- Unbounded work: lists, observers, timers, animation loops, requests, DOM nodes, database queries, memory, and retained objects.
- Hot paths: repeated parsing, duplicated calculations, layout reads mixed with writes, per-event allocations, unnecessary network waterfalls, and avoidable render churn.
- Lifecycle: listeners, resources, subscriptions, tasks, and cleanup when views unmount or leave the viewport.
- Build correctness: dependency graph, cache inputs, generated outputs, environment-dependent behavior, and stale artifacts.

Choose the simplest intervention that addresses the actual cost. Bounded pagination, static previews, indexed queries, conditional imports, and removing duplicate work often beat an elaborate optimization framework. Explain visible tradeoffs before making them when the user asked to preserve the interface. Do not silently change interactions, animation character, or image quality to obtain a better number.

Use the right evidence. A production bundle measurement is not a runtime benchmark. A smaller source file is not proof of lower latency. A passing build is not proof of browser behavior. A 30-item fixture is not proof of million-item scalability. A cache is useful only when every relevant input can invalidate it.

**FAST AND HIGHLY EFFICIENT means fewer real costs and reliable behavior, not performance adjectives.** Report before/after results where measured. Otherwise say exactly what waste was removed and what remains unmeasured.

## Make safe extension the normal path

### Replaceable frontend, protected backend

When starting an application codebase, make frontend/backend ownership explicit from the outset. Different contributors may own the UI and backend. A visual rewrite should consume a stable, documented contract without moving authorization, business rules, persistence, orchestration, or secrets into presentation code.

Keep frontend presentation, the client integration layer, shared contracts, backend logic, and generated bindings in clearly named locations appropriate to the actual stack. Use one repository unless another structure is justified; separation does not require microservices or separate repositories. Document the supported client operations, data/state shapes, errors, readiness/reconnect behavior, and verification commands. Explain which files a UI-only contributor may replace and which contract changes need coordination.

Enforce the separation with types, import boundaries, and meaningful integration tests. UI edits must preserve identity, subscription lifecycle, stale-revision checks, and user-visible failure states. Keep a short developer map and a single shared instruction source so another developer or model can navigate the code without private context. Apply this proportionally; do not scaffold speculative layers for small tools.

Give contributors a working example or generator when repeated additions have a real contract. Keep templates readable as templates, not huge opaque strings embedded in a CLI. Validate metadata, names, references, and generated artifacts. Refuse to overwrite existing work. Distinguish draft work from public output when the product needs that distinction.

Keep generated files visibly separate and mark them as generated. Fix the generator when output is wrong. Do not make agents manually synchronize the same fact across many files.

Maintain a short human entry point, an architecture/ownership map, a repeatable workflow, and clear verification commands. Use one shared instruction source for Claude and Codex with thin entry points. Do not duplicate entire instruction manuals by model. A contributor should know what can change locally, what is shared, what is generated, and what must be checked.

Be candid: instructions cannot guarantee that an agent never makes a mistake. Good interfaces, validation, type checks, tests, review, and reversible changes reduce the chance and catch failures before publication.

## Audit and fix in evidence-driven passes

1. Inventory the real structure, versions, scripts, dependencies, entry points, and existing tests.
2. Find concrete issues. Separate bugs, maintenance friction, measured performance costs, and optional preferences.
3. Prioritize failures, data loss, broken contracts, unsafe dependencies, and scaling hazards before cosmetic rearrangement.
4. Make focused changes, retaining stable public behavior unless the user requested a change.
5. Use tests that exercise actual behavior and catch plausible regressions. Test edge cases that matter: empty input, invalid metadata, duplicates, stale state, failed I/O, and bounded growth.
6. Verify changed user flows in the appropriate runtime. For frontend work, inspect desktop/mobile, keyboard behavior, both themes where supported, reduced motion, and errors. For tooling, run the commands against controlled fixtures.
7. Review the complete diff, documentation, references, and generated artifacts. Remove temporary files and accidental scope expansion.
8. Report the result, the remaining limits, and the next action only if one remains necessary.

Use relevant domain skills when they add useful guidance. Inspect a discovered third-party skill before installing or following it. Do not install many overlapping skills to simulate thoroughness. Avoid framework migrations and major dependency upgrades purely to say everything is newest; update where support, security, compatibility, or a real requirement warrants it.

## Final gate: do not call it clean until it earns the claim

Can a new person or model find the right owner, make a normal change, run it, verify it, and understand the result without private context? Can the code grow without multiplying manual wiring or always-on runtime work? Is the organization simpler to explain now? Are build/cache assumptions correct? Do docs match reality? Are claims supported by actual checks?

If not, keep fixing the concrete problem or state the specific remaining limitation. Do not hide unfinished work behind a beautiful README. Do not call an untested rewrite durable. Do not call extra layers professional simply because they look sophisticated.

**Clean, readable, navigable, maintainable, efficient. Again: clean, readable, navigable, maintainable, efficient. That is the standard. Achieve it through clear ownership, straightforward code, bounded work, and verified behavior.**
