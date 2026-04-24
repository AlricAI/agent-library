# **Cursor Agent Rule: Modular Core/Adapter Monorepo Architecture**

> description: Express.js hexagonal architecture with functional DI patterns and modular structure globs: - "apps/\*\*/\*"

## Tags
`typescript` `prisma` `postgres`

## System Prompt
---
description: Express.js hexagonal architecture with functional DI patterns and modular structure
globs:
  - "apps/\*\*/\*"
  - "packages/\*\*/\*"
scopes:
  - monorepo
  - backend
  - express
  - node
  - functional-di
  - tdd
alwaysApply: true
---

# **Cursor Agent Rule: Modular Core/Adapter Monorepo Architecture**

**Objective:** Maintain a highly modular, decoupled, and testable TypeScript monorepo. All platform-agnostic business logic ("Core") **must** be extracted into `packages/*`. All platform-specific entry points ("Adapters," e.g., `apps/api-server`) **must** be thin wrappers that consume the Core.

**Core Principle:** This architecture is a form of  Hexagonal (Ports & Adapters) Architecture.

* **The "Core" (`packages/core-*`):** This is your application's "engine." It contains all business logic, services, repositories, and domain types. It has **zero knowledge** of the outside world (i.e., no imports from `express` or any other platform-specific library).
* **The "Adapters" (`apps/*`):** These are the "delivery mechanisms." They are thin wrappers that translate platform-specific I/O (HTTP requests, CLI commands, etc.) into method calls on the Core. They are responsible for DI, composition, and error translation.

## **1. Monorepo & Project Structure**

* **Layout:** Use pnpm workspaces.

    ```txt
    / (root)
    ├─ package.json        # defines workspaces: ["apps/*", "packages/*"]
    ├─ pnpm-workspace.yaml
    ├─ tsconfig.base.json  # Base TS config with path aliases
    ├─ apps/
    │   └─ api-server/     # Express API Adapter
    │
    └─ packages/
        ├─ core-feature-users/ # Core: "Users" Bounded Context
        ├─ core-feature-posts/ # Core: "Posts" Bounded Context
        └─ core-db/            # Core: Shared DB client/schema
    ```

* **Package Decision:**
  * If code is platform-agnostic (business logic, data access, utilities), it **must** go in a `packages/core-*` library.
  * If code is platform-specific (HTTP routes, middleware, e

*[truncated — see source for full prompt]*