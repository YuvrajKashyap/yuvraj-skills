---
name: create-engineering-team
description: Create or repair a project's standing frontend, backend/technical-lead, code-review, testing, and production tasks with a shared product handoff and clear ownership. Use when the user asks to set up their engineering team for a project. Does not launch teams merely because a project is opened or authorize product changes by itself.
---

# Create an engineering team

Create a small, coordinated team for the actual project, not five competing rewrites. These are persistent user-facing tasks, not temporary subagents. Use the application's task-creation tools only when the user explicitly requests the team. A normal coding request is not team-creation permission.

## Team design

Read [roles.md](references/roles.md) fully before constructing role prompts. Default roster:

1. Backend engineer and technical lead: system design, authoritative behavior, and coordination.
2. Frontend engineer and design lead: the complete user experience.
3. Independent code reviewer: evidence-backed review, not self-approval by the builder.
4. Testing engineer: complete journeys, failure cases, and reproducible acceptance evidence.
5. Production engineer: safe releases and reliable operation.

Five available roles do not mean five constantly running agents. Use only roles relevant to the current change. The technical lead builds and coordinates; it does not dictate visual taste or waive independent review. Do not add a separate manager layer or specialist task without a concrete need and user authorization. For projects without a conventional UI or server, adapt those two roles to interface/client and core/system ownership rather than inventing a web app.

Read the [branch workflow](references/branch-workflow.md) when the team needs isolated working copies and review. Follow the repository’s existing conventions.

## Discover before creating

When refreshing an existing team, assess its roster and current project evidence without starting new turns unless the user asks to resume work. Read applicable saved operating preferences. Consult skill-synthesis for a substantial refresh; use current tool schemas and official documentation rather than copying an old task-creation payload. The app's available tools determine what can actually be created or resumed.

1. Read the conversation's latest decisions, repository instructions, README/status, product spec and relevant architecture/release notes. Inspect Git state without resetting anything. Keep requirements, proposals, shipped code, and prior test reports distinct. Never transfer secrets or personal records into prompts.
2. Use `list_projects` to resolve the exact project and host. Use existing task listings and any project team roster to identify existing roles. Match project/path and role, not title alone. Reuse suitable tasks; only create missing or explicitly requested replacement tasks. Do not unarchive, retitle, delete or move unrelated tasks. If a creation call has an uncertain result or pending client ID, reconcile before retrying; never create duplicates as a timeout workaround.
3. Identify the requested mode: team setup/orientation, assessment, or an explicitly approved implementation assignment. Team creation alone defaults to read-only orientation. Historical broad build requests do not override a newer assessment-first instruction.
4. Keep a small project-local team document, preferably `docs/engineering-team.md` if consistent with the repository. It holds the shared purpose, role ownership, actual task IDs/host/path, coordination procedure, current authority and current work assignments. Update an existing equivalent rather than creating a second source of truth. Do not overwrite existing instructions. Avoid placing project-specific facts in this global skill.

## Branch and review working agreement

Include these rules in every task prompt and the project team document:

- Everyone can read the entire project. Role ownership guides changes, not knowledge silos. Organize code around meaningful product behavior, not an artificial folder per engineer.
- The lead assigns each approved change an owner, exact working directory/branch, write scope, dependencies and acceptance criteria. Each writer verifies its directory and branch before editing. Shared interfaces still need agreement; separate copies prevent overwrites, not incompatible designs or merge conflicts.
- Keep one editor for the coordination board and one integrator for `main`. Builders commit only their own assignment in their own copy. Never reset, stash, clean, switch branches or stage another agent's checkout. A Markdown board is coordination, not a filesystem lock.
- Keep package installs and generated build outputs local to each copy. Reserve shared ports, test databases and provider targets explicitly; copies do not isolate those resources. Never kill an unowned process, copy production credentials by default or run against live data to make a test pass.
- Use one PR per bounded assignment. The independent reviewer handles the queue one PR at a time, with a verdict tied to the current base and head commits. The owner fixes findings. Changed code, a changed base or conflict resolutions require renewed review/checks. QA validates the combined candidate before the integrator accepts it.
- The reviewer accepts or requests changes; the designated integrator performs authorized merges. A role title, green checks or a review does not authorize deployment. Verify actual GitHub enforcement and identity limitations; instructions alone are not branch protection.
- After merging and checking the combined result, retire that assignment's worktree and local/remote branch safely. Preserve unmerged work and ignored data. Recreate the role-named branch from current `main` for its next assignment. When all work is accepted, only `main` remains; do not delete unfinished branches just to satisfy tidiness.
- Findings name evidence, impact and a reproducible check where possible. Distinguish release blockers from optional preferences. The original owner fixes issues; reviewer/QA do not become uncoordinated extra implementers.
- Resolve technical disagreements with evidence and the product contract. Escalate material product/security/cost decisions or unresolved disagreement to the user. No endless message loops or majority-vote truth.
- Cross-task messages stay within the authorized team and assignment. A skill is not a background scheduler: no automatic wakeups, monitoring, spawning or recursive delegation unless separately requested. Do not promise coordination is enforced by the app when it is only an instruction protocol.

## Construct and launch

When requested, brainstorm-to-frontend and brainstorm-to-backend can prepare the respective handoffs. Feed them the existing roster, assigned working copy and branch/review agreement. Do not run a second independent creation workflow or give each owner a competing product plan.

Each self-contained prompt must carry: canonical project and actual assigned working-copy path; branch and assignment ID; product purpose and exclusions; source documents and dated baseline; user preferences and starter-kit freedom; own role charter; counterpart responsibilities; branch/review rules; current permission and stopping point; useful available skills; and the requested first deliverable. Use domain-relevant skills on demand instead of dumping every skill into every context. Never assume the receiving task inherits conversation history.

Use actual tools and their schemas, not invented agent configuration APIs. Do not override model or reasoning settings unless the user asks. Create persistent tasks with the application's `create_thread` when available. Do not use temporary subagents as a substitute for requested user-owned chats.

Record each creation result immediately. A clientThreadId is pending, not a usable threadId. Resolve ready IDs through supported task listings; never feed client IDs to tools that require thread IDs. Update the roster with verified IDs only. If setup is pending, say so, avoid duplicate retries, and leave enough information to resume.

For orientation-only starts, ask each role to read its charter and key project documents, return a concise ownership summary and a few evidenced priorities, then stop. No app edits, provider mutations, production tests, deployments or new agents. Read-only reviews can run together; shared builds cannot.

After creation, verify actual cwd/host and use one bounded `wait_threads` call for ready tasks to confirm progress; do not wait on pending IDs. Correct a wrong setup through supported tools and explicit authority, never hide it. Report created versus reused versus pending roles and any gaps. Do not claim that registration alone makes an autonomous, always-running team.

## Check the result

- For a resumed project, record what changed since the last checkpoint and which old test/release claims need refreshing. Check dependencies and client compatibility before calling the environment ready; upgrading the skills is not upgrading the app.
- All roles map to the same repository. Concurrent writers have verified separate working copies and branches. Read-only roles may inspect stable copies without a permanent branch. An explicit shared-folder exception requires non-overlapping writers and one build/Git operator.
- No duplicate roles, fabricated IDs, copied credentials or silently expanded execution permission.
- Product intent survives; implementation remains revisable; real users and data remain protected.
- Lead coordination, independent review, QA acceptance and release ownership are distinguishable.
- The project roster is discoverable and prompts remain usable without the source chat.
- The first task responses follow their scope. If a role starts unauthorized edits, stop that work before proceeding rather than declaring setup successful.

The creation workflow can be tested without external writes using a supplied fake project inventory/task roster. Useful cases: an existing partial team; a dirty shared checkout; a pending creation; a non-web project; and a request to discuss a team without creating it. Check decisions and actions, not exact prose.
