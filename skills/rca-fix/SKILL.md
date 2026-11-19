---
name: rca-fix
description: Turn an established root cause into a narrowly targeted repair and a regression check.
---

# Rca Fix

Read the causal finding and confirm it still applies to the current revision. Encode the failure at the lowest layer that retains the real trigger. Show the failing result before modifying behavior when feasible.

Repair the component that owns the violated invariant. For example, if retrying an already-saved operation duplicates a row, establish stable operation identity at the persistence boundary and check what both callers receive. Check that a genuinely new operation still succeeds.

Repeat the original user journey, then exercise the closest valid neighboring case. Report the before-and-after evidence and whether any existing records require separate recovery.
