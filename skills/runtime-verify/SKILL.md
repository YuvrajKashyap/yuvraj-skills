---
name: runtime-verify
description: Verify a claimed behavior through the running application and distinguish direct evidence from simulated coverage.
---

# Runtime Verify

Write the claim as something an observer can test. Record the running revision, environment, dependencies, and data isolation. Choose a normal entry point and the smallest input that can produce a distinctive result.

Observe both the user-facing response and any durable effect the claim entails. For a saved preference, change it through the UI, reopen the application, and verify the displayed value. If syncing is part of the claim, check a second authorized client. A mocked sync response supports only the local branch.

Record the exact result, unexpected side effects, cleanup, and verification limits. If a dependency is unavailable, state which part of the claim remains open.
