# Choose skills for a project

This is a selection guide, not a requirement to load every listed skill. Resolve names against the current available catalog, read selected instructions fully, and use their relevant references. Availability and plugin names can change. Do not install replacements just because a named skill is unavailable.

## Start with the outcome

1. Read the product decisions, repository instructions, current implementation and applicable saved preferences. Separate decisions needed from the user from engineering choices the agent can make.
2. Use skill-synthesis for a substantial new workflow or refresh. Use find-skills only when discovery adds something beyond the installed catalog.
3. Use codebase-design for module/interface choices and clean-codebase for readable, navigable implementation. Plain-English communication takes precedence over specialized vocabulary in source skills.
4. If the user requests persistent engineering tasks, use create-engineering-team. Reuse an existing roster. Its current default is one repository, grouped separate working copies, short-lived assignment branches named for project/chat, sequential PR review and cleanup back to main. Read its branch-workflow reference when setting up or migrating that process. For one small project or a bounded change, a single agent may be enough; do not spawn a team just to follow a checklist.
5. Use brainstorm-to-frontend or brainstorm-to-backend when transferring product context to those owners. They complement the team skill; they are not additional teams or mandatory startup steps.

## Select by the work being done

| Work | Available skill families to consider |
| --- | --- |
| Challenge uncertain product decisions | grilling, only when that questioning style is requested |
| Visual direction | frontend-design, impeccable, or one relevant frontend-design variant; select one primary design voice |
| Phone interaction | mobile-frontend; max-frontend when its requested high-polish scope applies |
| Motion | emil-design-eng, animation-vocabulary, improve-animations or review-animations according to the task |
| Existing app performance | invisible-performance for no-visible-change work; measure rather than assume improvements |
| React composition and performance | vercel-composition-patterns, vercel:react-best-practices |
| Database and account behavior | supabase:supabase and relevant supabase-postgres-best-practices references |
| User-supplied agents and tools | mcp-builder, plus current protocol/SDK documentation |
| App-supplied AI | vercel:ai-sdk or vercel:build-agents only if the product actually supplies intelligence |
| Python or other backend | fastapi, python-testing or elysiajs only for the chosen stack |
| Implementation tests | test-driven-development or tdd as the primary test workflow; reconcile overlapping instructions, do not run duplicate processes |
| Browser and accessibility checks | webapp-testing, web-accessibility-quality-audit or web-design-guidelines |
| Security review | security-best-practices, security-threat-model when their review scope is needed or requested |
| Release and operation | current vercel deployment, environment, storage, firewall and verification skills as relevant |
| Final evidence | verification-before-completion |
| Reusable workflow improvement | skill-creator; skill-installer only for authorized installation |

Other project types have separate skills: native iOS, computer vision, documents, spreadsheets, presentations, data analysis, video, design assets and Notion project setup. Do not force web engineering roles or web tooling onto them. Duplicate catalog names can point to the same underlying files; inspect before deleting or updating either path.

## Refresh after time away

- Inspect Git status and last recorded results. Never call an old passing run current evidence.
- Check official framework/provider changes, security advisories, supported runtime and actual client compatibility. Verify dates instead of assuming that a new month implies a new best practice.
- Prefer exact version pins and a reviewed lockfile change. Separate security patches from optional framework changes and provider CLI major upgrades.
- Check local-versus-live settings without printing secrets. Do not start a test that writes to a real account merely because it runs on localhost.
- Distinguish skills ready, local environment ready, core journeys tested, and release approved. Passing one is not passing all four.
- If only skills/preparation are authorized, update those artifacts and identify the first implementation step; do not silently upgrade packages, change cloud access, launch tasks or deploy.

## Helpful primary references

Recheck when relevant rather than treating this list as a permanent version snapshot.

- [OpenAI skills guidance](https://learn.chatgpt.com/docs/build-skills) for focused instructions and on-demand loading.
- [OpenAI subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents) for bounded delegation and the cost of simultaneous code edits.
- [Next.js agent guidance](https://nextjs.org/docs/app/guides/ai-agents) for version-matched bundled documentation and runtime feedback.
- [Supabase changelog](https://supabase.com/changelog) for breaking provider/CLI changes.
- [MCP security guidance](https://modelcontextprotocol.io/specification/latest/basic/security_best_practices) for authorization and cross-client isolation.

These references inform execution, not permission. A skill refresh never authorizes installs, account access changes, public publication or legal conclusions by itself.
