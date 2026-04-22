# MIGRATION

> This plan is scoped to client-only.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Client Migration Plan

This plan is scoped to client-only. Update the checklist as work completes.

## Phase 1 - React Upgrade (no refactors)

Goal: Run on latest React with minimal code changes.
Checklist

-   [x] Bump core React packages (react, react-dom, react-test-renderer)
-   [x] Align React ecosystem deps:
    -   [x] react-redux
    -   [x] react-dnd + react-dnd-touch-backend
    -   [x] react-transition-group
-   [x] Align UI deps:
    -   [x] react-bootstrap
    -   [x] react-bootstrap-typeahead
    -   [x] react-select
    -   [x] react-toastify
    -   [x] bootstrap (bump to v5 to align with react-bootstrap v2)
-   [x] Test tooling: N/A (legacy client Jest/Enzyme removed)
-   [x] Ensure client entry points still render: client/index.dev.jsx, client/index.prod.jsx
-   [x] Fix build/runtime breakages only (no refactors)

Potential blockers and checks

-   react-bootstrap-select not found in client (no matches on scan)
-   react-bootstrap-typeahead is an old alpha; confirm compatibility or pin React to a supported range
-   react-bootstrap-table\* packages historically lag React majors; replace with a custom table
-   enzyme is React-16-era; may require moving tests to react-testing-library or disabling legacy tests
-   legacy React 16 UI deps replaced during Phase 1:
    -   react-redux-toastr -> react-toastify
    -   react-bootstrap-table\* -> custom table in DeckList
    -   react-select v3 -> v5
        Status: deps match Phase 1 targets (React 18.2, react-redux 8.1.x, react-dnd 16, react-select 5.10, react-bootstrap 2.10 + bootstrap 5.3); runtime fixes landed (corrupted imports, react-dnd drag type, DeckList table/style regressions). Pending: react-router is not yet introduced (custom router remains), entry-point smoke check still needed.

Phase 1 target versions (as of 2026-01-29)

-   React core:
    -   react: 18.2.0 (target for Phase 1 to reduce peer conflicts)
    -   react-dom: 18.2.0 (align with react)
-   React ecosystem:
    -   react-redu

*[truncated — see source for full prompt]*