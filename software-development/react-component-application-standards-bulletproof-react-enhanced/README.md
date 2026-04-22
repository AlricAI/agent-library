# React Component & Application Standards (Bulletproof‑React Enhanced)

> description: Comprehensive React component and application standards globs: - "**/*.tsx"

## Tags
`typescript` `react` `redis` `netlify`

## System Prompt
---
description: Comprehensive React component and application standards
globs:
  - "**/*.tsx"
  - "**/*.jsx"
scopes:
  - react
  - frontend
  - ui
  - components
alwaysApply: false
---

# React Component & Application Standards (Bulletproof‑React Enhanced)

> **Purpose**  Unify front‑end architecture, state, logging, testing, and DX across every app in `/apps/*`, combining our existing guide with proven *Bulletproof React* principles.

---

## 1  Project Layout & Dependency Flow

```text
src/
  app/           # React Router entry (Vite CSR), global providers
  features/      # Self‑contained domain slices (Auth, Billing…)
  components/    # Re‑usable UI primitives (Button, Card…)
  hooks/         # Shared hooks not tied to a feature
  lib/           # Framework‑agnostic utilities (date, math…)
  types/         # Global TypeScript contracts
```

* **Unidirectional flow**  `components → features → app` only (enforced via ESLint `import/no-restricted-paths`).
* **Absolute imports**  Configure `@/*` alias in `tsconfig.json` to eliminate `../../../`.

## 2  Code Quality Guard‑Rails

| Tool                                                 | Purpose                  | Invocation                    |
| ---------------------------------------------------- | ------------------------ | ----------------------------- |
| TypeScript `--strict`                                | Static safety            | `pnpm tsc -p tsconfig.json`   |
| ESLint (+ plugin\:import, plugin:@typescript-eslint) | Style & dependency rules | `pnpm lint`                   |
| Prettier                                             | Auto‑formatting          | `pnpm format`                 |
| Husky + lint‑staged                                  | Pre‑commit gate          | runs `lint`, `format`, `test` |

CI workflow → *fail fast* on lint, type, unit, integration, e2e.

## 3  State Management – Four Buckets

1. **Local component state**   `useState`, `useReducer`.
2. **UI / app state**          Context, Zusta

*[truncated — see source for full prompt]*