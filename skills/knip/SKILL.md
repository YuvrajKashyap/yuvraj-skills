---
name: knip
description: Investigate unused JavaScript or TypeScript files, exports, and dependencies with Knip.
---

# Knip

Inspect the workspace manifests, existing Knip configuration, entry points, and package manager. Prefer the repository's installed version and existing analysis command. Record the initial findings before touching files.

Trace likely false positives through package exports, framework conventions, dynamic imports, code generation, examples, and commands invoked only by CI. Treat exported library APIs as potentially consumed outside the checkout. Model a missing entry point in configuration when that explains several findings.

For authorized cleanup, make a small coherent removal, run the affected build or consumer, and compare the next Knip result with the baseline. List uncertain findings separately with the evidence needed to resolve them.
