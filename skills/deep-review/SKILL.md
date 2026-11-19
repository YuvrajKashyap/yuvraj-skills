---
name: deep-review
description: Review an implementation across its user-visible contract, data flow, and failure paths before integration.
---

# Deep Review

Pick a consequential change and follow it from the normal entry point to its durable effect. Read callers on both sides of a changed interface. Identify who can invoke it, what existing data it must accept, and what a caller sees if the final write succeeds but its response is lost.

Choose a concrete example that could disprove each suspected problem. For example, when reviewing a rename operation, open a second view before the rename and check what happens when that stale view saves. Use fixtures appropriate to the project. Trace uncertainty to a file, transaction boundary, or missing test.

Report findings in order of user impact. Include the triggering conditions, expected and observed behavior, evidence location, and a narrow verification step. If no issue survives inspection, name the paths reviewed and the most important untested scenario.
