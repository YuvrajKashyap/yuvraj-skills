# Temporary branches, review and cleanup

Read this when implementing or changing the team's Git workflow. Keep project facts in its existing engineering-team document, not in this reusable skill. The aim is safe, understandable delivery with `main` as the lasting source of truth.

## Layout and naming

- Prefer keeping the existing project checkout in place as `main`. Group assignment copies in an ignored project-local directory. For a newly organized project, a container with `main/` and `worktrees/` is also reasonable; do not move an established project just for symmetry.
- Use supported app worktree tools when available. Inspect their current schema. If the app chooses storage and offers no target path, leave its managed storage intact and create a project-local directory of links if appropriate. Record physical paths and links separately. Do not edit the app's internal database or pretend a prompt changed a chat's working directory.
- If creation/attachment applies only to the calling chat, have each authorized owner create or attach its assigned copy from the preserved assignment ref, then report its verified path/branch/commit. Do not create every copy in the coordinator chat and claim the owners were moved. Keep the shared source frozen until these confirmations arrive; reconcile pending operation IDs before retrying.
- Links/grouped copies must be ignored by Git, recursive tests, formatters, type checking and build/upload tools. No recursive copying of the project into itself. Do not share `.next`, writable `node_modules`, test reports or environment files across copies.
- Name each temporary branch `<project>-<normalized-chat-name>`. Validate using `git check-ref-format --branch`. Preserve the actual chat title in the roster. An active name collision means reuse that exact assignment or wait, never overwrite the branch. For simultaneous assignments owned by the same chat, serialize by default; use an explicit assignment suffix only when needed and agreed.
- `main` is the only lasting branch. A reviewer normally needs a detached, read-only copy, not a permanent reviewer branch. QA/prod get branches when they are changing files, not merely because they exist on the roster.

## Migrate unfinished shared-folder work

1. Ask current writers to finish only an atomic write/fixture cleanup, record owned files, tests, active resources and remaining dependencies, then stop. Verify they stopped; a pause request alone is not proof.
2. Inventory staged, unstaged, untracked and ignored state separately. Identify other people's edits and generated files. Keep the actual index and source unchanged while preserving a local recovery copy with hashes; exclude credentials, local databases, account records and transient logs from Git objects and PRs. Private ignored files may remain in place.
3. Assign every captured source change to an owner. Split by real dependencies and reviewable behavior. If changes cannot safely be separated, keep the combined source intact and document a narrowly justified shared foundation; do not represent unfinished combined work as approved `main`.
4. Local WIP commits may preserve incomplete work if clearly labeled. They are not evidence that tests pass. For necessary stacked changes, record their parent/base explicitly. Prefer independent assignments from current `main` once the migration is complete.
5. Create/attach working copies using supported tools; verify repository identity, absolute physical directory, branch and initial commit for each. Copy only assigned changes. Verify hashes and staged/unstaged preservation before any source cleanup. A failed operation or changed file stops cleanup, not preservation.
6. Keep the old mixed checkout frozen until its changes are recoverable and the source can be reconciled without loss. Never blanket reset, stash, clean, force switch or delete a dirty worktree as migration machinery.

## Assignment and PR flow

Record a compact queue: assignment ID, owner/chat, branch, worktree, base/head commits, dependency, PR, reviewer verdict, checks, merge and cleanup state. One editor owns that queue. Exact commits identify evidence; titles and branch names can be reused.

1. Start from current `main`, or explicitly record a dependency branch for stacked work. Define a bounded complete behavior, owner and acceptance checks. Coordinate API/schema changes before parallel implementation.
2. Builder uses only its working copy. Run appropriate checks and inspect the diff before committing. Keep secrets, private records, runtime fixture databases and generated output out of Git; intentional synthetic test source/fixtures belong in review. A draft PR can honestly show incomplete work; do not mark it ready while known acceptance blockers remain.
3. Inspect push side effects before publishing. A push/PR can start CI, paid usage or a preview connected to a live database. Scope existing authorization precisely. Hold unsafe deployment integration rather than bypassing privacy checks. Do not silently spend money, change visibility or weaken controls to enable the workflow.
4. Reviewer processes one stable PR at a time. Read the requirement, complete diff and relevant surrounding code; independently check failure paths. Record `accept`, `changes requested` or `blocked on evidence` against both base and head commits. Identify concrete findings without inventing a quota. Builder fixes; reviewer rechecks. Reviewer's own code changes require another independent reviewer.
5. Integrator updates the candidate against current `main`. Any conflict resolution is new code to inspect and test. QA checks the exact combined candidate. For a moving base, refresh relevant review and checks; a green old branch is not proof of the combination.
6. Merge one PR at a time only after required review/checks and applicable authority. If merging/pushing main automatically deploys, treat that merge/push as deployment too and require matching authorization or an approved way to hold deployment first. Verify resulting `main`, hosted CI where used, and acceptance results. Stop subsequent merges on failure; repair or revert with preserved work. Do not infer publication authority from a review verdict.

## Real enforcement, not imaginary guarantees

- Distinguish agent independence from GitHub identity. Two chats using the same GitHub account cannot provide author-independent GitHub approvals. Record independent agent review as evidence; do not fabricate a separate reviewer account or claim it satisfies required approvals.
- Inspect repository visibility, plan and actual protection/rulesets. Configure protections only within authorization and available features. If the plan cannot enforce them, say so and use a named integrator plus a review/check gate, while explicitly stating that any identity with sufficient push access can bypass a procedural gate.
- Required checks should cover meaningful project tests and the combined candidate. Do not use `pull_request_target` to execute untrusted PR code with secrets. Use least-privilege workflow permissions. A job named "review" is not an independent code review.
- Branches isolate file edits; they do not isolate ports, database state, cloud resources, machine memory or contract design. Assign shared resources and use synthetic fixtures. No claim of eliminating every conflict or bug.
- Give heavy builds, browser suites, database loads and benchmarks a runner slot. Start with one heavy job on a shared desktop; allow overlap only after checking available memory, worker counts and measured headroom. Separate ports alone do not establish safety. Keep ordinary editing and independent light checks parallel. Cap build workers through supported configuration when default CPU-based fan-out exceeds the machine's memory. Preserve failures observed under contention and reproduce them with adequate resources before classifying them; never hide them with skipped assertions or inflated timeouts.
- Package and browser updates can affect shared caches outside a working copy. Check the upstream fix and released version, pin the selected dependency, preserve older binaries still used by another assignment, and rerun the same failing behavior. Record tool limitations separately from application defects and physical-device acceptance.

## Close the assignment

Before removing a copy or branch, verify: merged PR and exact accepted head; combined `main` checks finished; no active process; no dirty/untracked work or needed ignored data; no dependent PR still targets this branch; no other chat owns the copy. Compare ancestry or the squash/rebase result as appropriate. Never force-delete merely because ancestry differs after squash.

Use `archive_worktree` for managed copies, following the app's supported lifecycle. Remove only the matching local link after checking its resolved path; do not recursively delete through a Windows junction. For unmanaged copies, use Git worktree removal, never blanket filesystem cleanup. Delete only the completed assignment's local and remote refs when authorized, then verify both branch lists. A recoverable archived copy is not an active branch. Do not archive user chats unless asked.

If anything remains unmerged or uncertain, retain it and name the reason. Clean up automatically once conditions are met under the user's stated cleanup instruction; do not repeatedly ask to do what they already authorized. A later assignment recreates the role-named branch from fresh `main`.

## Behavioral checks when refreshing this workflow

Use realistic isolated examples: mixed dirty checkout; two tasks changing one interface; a pending worktree creation; stale review after a new commit; tests passing individually but failing together; same-account self-approval; private plan lacking protection; squash merge with a dirty copy; stacked PR still targeting a branch; a Windows junction pointing outside the project; and all assignments done with only `main` remaining. Validate decisions and actual Git state, not wording.

## Primary references

- [Git worktree](https://git-scm.com/docs/git-worktree): separate working trees share repository refs; a branch normally cannot be checked out twice.
- [GitHub required reviews](https://docs.github.com/en/pull-requests/how-tos/review-pull-requests/approving-a-pull-request-with-required-reviews): authors cannot approve their own PR; stale reviews and enforcement depend on configuration.
- [GitHub protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches): inspect current plan support and settings.
- [Codex worktrees](https://learn.chatgpt.com/docs/environments/git-worktrees): follow current app lifecycle and actual available tool schemas.

Recheck dynamic provider behavior at use time. References do not authorize external actions.
