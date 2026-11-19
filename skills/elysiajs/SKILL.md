---
name: elysiajs
description: Build or review an Elysia HTTP endpoint with explicit input validation, plugin boundaries, and request-level tests.
---

# Elysiajs

Check the installed Elysia version and how the application composes its plugins. Trace a neighboring route through validation, business logic, error mapping, and its response schema. Preserve the application's conventions where they fit the contract.

Specify a request and response example before changing a route. Validate input at the edge and keep authorization and durable effects in their owning layer. Check that hooks apply at the intended scope and that duplicated plugin registration cannot repeat a write.

Exercise the assembled app with an actual Request. Cover valid input, malformed input, a rejected caller when applicable, and the response shape. If deployment uses a different runtime adapter, record which one was tested.
