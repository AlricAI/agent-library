# Monorepo Structure and Configuration (v4)

> description: Core monorepo structure, ESM-only, no-build libraries, shared config, agent coordination globs: - "**/*"

## Tags
`typescript` `javascript` `react` `stripe`

## System Prompt
---
description: Core monorepo structure, ESM-only, no-build libraries, shared config, agent coordination
globs:
  - "**/*"
scopes:
  - monorepo
  - global
---

# Monorepo Structure and Configuration (v4)

## ⚠️ CRITICAL STRUCTURAL UNDERSTANDING

This document contains ESSENTIAL information about how the monorepo is structured and the development philosophy behind it. It must be understood for ALL operations in the codebase.

### Core Principles

1.  **ESM-Only:** We exclusively use ES Modules. CommonJS (`require`, `module.exports`) is not used. This simplifies our tooling and aligns with the modern JavaScript ecosystem.
2.  **No Build Step for Libraries:** Packages in `/packages` are not "built" into a `dist` folder. We export TypeScript source files (`.ts`, `.tsx`) directly. A runtime transpiler (like `tsx`) handles this for us, enabling instantaneous hot-reloading and simpler debugging.
3.  **Configuration is SHARED:** All tooling configuration (ESLint, Prettier, TypeScript, Testing) is centralized in the `/tooling` directory and consumed by all other workspaces. **DO NOT** create duplicate or one-off configurations.
4.  **Strict Naming & Structure:** Packages and folder structures follow a strict, predictable pattern. **DO NOT** deviate from it.
5.  **Agent Coordination First:** Before running any command, always check the `_errors/` and `_logs/` directories managed by `@kit/brain-monitor` to prevent redundant work.

### Devil's Advocate: Why No CommonJS?

You're right to want to keep things simple with ESM-only. But for the sake of completeness, here's the trade-off:

  * **Pros (Our Approach):** Massively simplified build process (or lack thereof), single module system to reason about, aligns with web standards, and enables cleaner, more modern syntax like top-level `await`.
  * **Cons:** Dropping CJS means older Node.js environments or tools that *only* support `require()` cannot consume our packages natively. Since we control the entire stack within this mon

*[truncated — see source for full prompt]*