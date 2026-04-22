# Igniter.js: Procedures (Middlewares)

> description: Provides the correct and validated pattern for creating and using procedures (middlewares) in Igniter.js. globs: src/features/**/* alwaysApply: false

## Tags
`typescript` `prisma` `redis`

## System Prompt
---
description: Provides the correct and validated pattern for creating and using procedures (middlewares) in Igniter.js.
globs: src/features/**/*
alwaysApply: false
---
# Igniter.js: Procedures (Middlewares)

This guide provides the **correct and validated** pattern for creating and using procedures (middlewares) in Igniter.js.

## 1. How Procedures Extend Context

Procedures in Igniter.js extend the context for subsequent actions by **returning an object**. This is a critical pattern to understand.

-   **DO NOT use `next(newContext)`:** Unlike frameworks like Express, you must not call a `next` function to extend context.
-   **RETURN an object:** The object you return from the procedure's handler will be shallow-merged into the `context` that the final action receives.
-   **Special Case: `next()` for Post-Action Processing**: The `next()` function in a procedure's handler should **only** be used if the procedure needs to capture and process the *result* of the subsequent action (e.g., for auditing, performance monitoring, or response modification). In such cases, `await next()` should be called, and the result should then be handled. Otherwise, procedures should either return an object to extend the context (e.g., `{ auth: { user } }`) or `void` (implicitly or explicit `return;`) to simply allow the request to proceed without modifying the context.
-   **Auth Procedure Context for Optional Authentication**: When an `authProcedure` is configured with `required: false` (or if authentication fails but is not strictly required), it **MUST** explicitly return an object like `{ auth: { user: null } }` to maintain consistent context typing, indicating that no authenticated user is present.

### ✅ Correct Example: `auth.procedure.ts`

This example demonstrates how to verify a user and add their information to the context, now leveraging globally injected services and repositories.

```typescript
// src/features/auth/procedures/auth.procedure.ts (Example - Refactored)


*[truncated — see source for full prompt]*