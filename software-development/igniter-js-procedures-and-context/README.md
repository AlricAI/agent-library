# Igniter.js: Procedures and Context

> description: | A guide to Igniter.js procedures and the context system. Explains how to create middleware for reusable business logic, dependency injection, and extending the request context in a type-safe manner. alwaysApply: false

## Tags
`typescript` `prisma`

## System Prompt
---
description: |
  A guide to Igniter.js procedures and the context system. Explains how to create middleware for reusable business logic, dependency injection, and extending the request context in a type-safe manner.
alwaysApply: false
---

# Igniter.js: Procedures and Context

This guide covers two core concepts in Igniter.js: the **Context** system for dependency injection and **Procedures** for creating reusable middleware.

## 1. The Context System

The Context is a type-safe dependency injection mechanism that makes global services and request-specific data available throughout your API layer.

### 1.1. Base Context
The base context defines services that are available in *every* request handler. It is defined once when you initialize the Igniter instance.

-   **File Location:** `src/igniter.context.ts`
-   **Purpose:** To provide singleton services like database clients, loggers, and other providers to your actions and procedures.

```typescript
// src/igniter.context.ts
export function createContext() {
  return {
    database: prisma, // Prisma client instance
    // ... other global services
  };
}

export type IgniterAppContext = ReturnType<typeof createContext>;

// src/igniter.ts
export const igniter = Igniter
  .context<IgniterAppContext>()
  // ... rest of the configuration
  .create();
```
Inside any action handler, you can now access `context.database` in a fully type-safe way.

### 1.2. Dynamic Context Extension
The real power of the context comes from its ability to be dynamically extended on a per-request basis. **Procedures** are the mechanism for this.

When a procedure returns a value, that value is deeply merged into the `context` object, making it available to all subsequent procedures and the final action handler. This process is fully type-safe.

## 2. Procedures (`igniter.procedure`)

A Procedure is a piece of reusable logic that runs before your main action handler. It is the Igniter.js equivalent of middleware. Procedures are ideal fo

*[truncated — see source for full prompt]*