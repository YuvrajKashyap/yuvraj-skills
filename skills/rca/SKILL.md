---
name: rca
description: Investigate an observed failure and identify the earliest causal divergence from expected behavior.
---

# Rca

Start with a precise observation and timeline. Separate what someone saw, what the system recorded, and what you currently infer. Write down the expected transition and locate the earliest stage where two comparable runs differ.

Keep competing explanations alive until a discriminating observation resolves them. If an export is empty, compare the input selection, serialized request, stored job, worker input, and final file. An empty file alone cannot distinguish a selection error from a worker error.

Return the causal chain, the evidence that supports each link, and a test that would disprove it. If you cannot identify the cause, report the boundary you narrowed it to and the next observation needed.
