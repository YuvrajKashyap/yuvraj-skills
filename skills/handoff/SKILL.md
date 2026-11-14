---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS (`$TMPDIR`, else `/tmp`; `%TEMP%` on Windows) - not the current workspace.

Include a "suggested skills" section naming applicable installed skills and their actual paths. The receiving agent should use its native skill loader when available, or read the named SKILL.md and relevant references with its file-reading tools. Do not assume a tool named Skill or a particular provider exists, or install missing skills automatically.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.

## Cross-provider handoff

Run only when the user requests a handoff. Preserve this explicit invocation intent even in hosts that ignore frontmatter invocation settings.

Use the host's temporary-directory API or environment variable rather than hardcoding an OS path. A user-specified destination takes precedence. If file writing is unavailable, return the handoff as text and state that it was not saved. Return the exact saved path when writing succeeds.

Capture the objective, accepted decisions, constraints, completed work and evidence, remaining work, relevant files or commits, and the next concrete action. Distinguish verified state from assumptions and old test results. Preserve the scope of existing authorization without extending it to new actions. Point to durable local project records instead of duplicating them. Do not send the handoff to another chat or service unless asked.

Before finishing, read back the file when one was saved and check that referenced paths are accurate and sensitive values are absent. The receiving agent should recheck mutable state before acting.
