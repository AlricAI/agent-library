# Next.js Middleware: Patterns & Best Practices

> description: When you need create a middleware to protect some page of Next.js app alwaysApply: false Next.js Middleware: Patterns & Best Practices

## Tags
`typescript`

## System Prompt
---
description: When you need create a middleware to protect some page of Next.js app
alwaysApply: false
---
# Next.js Middleware: Patterns & Best Practices

This guide provides the **correct and validated** patterns for creating and using Next.js Middleware within this project. The primary goal is to clearly separate concerns: Middleware handles routing and edge logic, while Igniter.js procedures handle backend business logic.

## 1. Core Principles

### 1.1. Separation of Concerns
-   **Middleware's Role**: Intercepting requests *before* they hit a page or API route. Its responsibility is to handle **routing, authentication checks, redirects, and request/response enrichment**. It acts as a gatekeeper.
-   **Procedure's Role**: Executing complex **backend business logic**. This is where database queries, integrations with other services, and heavy computations should live.
-   **CRITICAL RULE**: Middleware should **NEVER** perform heavy database operations. It can make fast API calls (like checking a session), but any complex logic must be delegated to an API endpoint that uses a procedure.

### 1.2. Performance: Edge vs. Node.js Runtime
-   Next.js 16 allows middleware to run in either the `edge` or `nodejs` runtime.
-   **Edge Runtime (Default & Recommended)**: Faster, runs closer to the user, but has limitations (e.g., no native Node.js APIs). Ideal for simple checks and redirects.
-   **Node.js Runtime**: Provides full Node.js API compatibility. Use this only if you absolutely need a specific Node.js API that the Edge runtime doesn't support. For this project, **we will stick to the Edge runtime unless there's a compelling reason to change**. The existing `middleware.ts` is already configured for `nodejs`, which is fine, but we should be mindful of its performance implications.

### 1.3. The `matcher`: Precision is Key
-   The `matcher` config property is crucial for performance. It defines exactly which paths will trigger the middleware.
-   An effective `mat

*[truncated — see source for full prompt]*