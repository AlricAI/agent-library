# Lint Rollout Plan

> _Last updated: 2025-11-28_

## Snapshot of the Current State

-   `npm run lint` executes `tsc --noEmit`; ESLint is not part of the automated workflow

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ESLint Rollout Plan

_Last updated: 2025-11-28_

## Snapshot of the Current State

-   `npm run lint` executes `tsc --noEmit`; ESLint is not part of the automated workflow.
-   The flat `eslint.config.ts` extends the base JS, TypeScript, and React recommended presets without repository-specific overrides.
-   Lint errors are not surfaced in CI; `npm run test` and `npm run build` both succeed even with style and correctness issues that ESLint would typically catch.
-   The codebase is large (React + TypeScript) with multiple feature folders (`animation/`, `audio/`, `export/`, etc.), so a full one-shot lint fix is impractical.

## Goals

1. Introduce ESLint as a first-class quality gate without disrupting ongoing feature work.
2. Drive the warning count to zero and keep it there.
3. Provide team-friendly tooling (editor integration + scripts + CI) so developers get fast feedback.
4. Avoid large, risky "big bang" refactors by shipping lint coverage in controlled slices.

## Guiding Principles

-   **Start non-blocking, end blocking.** First collect signal, then fail builds once the noise is removed.
-   **Prefer additive rules.** Begin with correctness and consistency rules that catch bugs, add stylistic rules only after buy-in.
-   **Make the cost visible.** Track lint error counts and show deltas in PRs/CI dashboards.
-   **Automate the guardrails.** Every new rule should have an associated autofix or documented resolution path.
-   **Measure success.** Each phase has an explicit exit criterion so we know when to move forward.

## Phase Plan

### Phase 0 — Foundation (week 0)

**Objectives**

-   Ensure ESLint is runnable locally and in CI.
-   Establish owner(s) and communication channels.

**Key Tasks**

-   Update `npm run lint` to run both `tsc --noEmit` and `eslint` (e.g., `npm run lint:types && npm run lint:eslint`).
-   Add a dedicated `lint:eslint` script: `eslint "src/**/*.{ts,tsx}" --max-warnings=0 --report-unused-disable-directives`.
-   Confirm editor i

*[truncated — see source for full prompt]*