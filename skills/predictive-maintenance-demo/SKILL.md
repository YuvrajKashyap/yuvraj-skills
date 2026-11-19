---
name: predictive-maintenance-demo
description: Build a simulated predictive-maintenance walkthrough with traceable sensor evidence and verifiable outcomes.
---

# Predictive Maintenance Demo

Choose a single piece of equipment and a measurable signal. Describe its units, sampling interval, expected operating range, and how missing readings appear. Use a small synthetic sequence with a normal window, a gradual deviation, and a recovery. Label the source of every displayed measurement.

Follow one deviation through the full experience. Show which observations triggered attention, a plausible alternative explanation, and what additional measurement would help. Keep a rule threshold distinct from a calibrated probability of failure.

Let an operator acknowledge the alert and create a simulated maintenance request. Give that request a stable identity so replaying the sequence cannot duplicate it. Validate an offline run, a missing-data window, and replay of the same event. Display the simulated status wherever the proposed action appears.
