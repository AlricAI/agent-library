# INSTRUCTIONS

> > **Authority:** This document is the execution authority for the frontend refactoring initiative.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend Refactoring — Codex Execution Instructions

> **Authority:** This document is the execution authority for the frontend refactoring initiative.
> It operates WITHIN the existing doc hierarchy defined in `docs/PROMPT_CANONICAL_SOURCES.md`.
> The UI canonical precedence in `docs/UI_CANONICAL_PRECEDENCE.md` still governs all visual/interaction conflicts.
> This document adds IMPLEMENTATION INSTRUCTIONS on top of existing design system references.

---

## How to Use This Package

This folder (`docs/frontend-refactor/`) contains everything needed to rebuild the `apps/web/` frontend.
Implement phases in strict order. Each phase produces deliverables consumed by later phases.

```
docs/frontend-refactor/
├── INSTRUCTIONS.md                   ← YOU ARE HERE — master execution guide
├── OPERATIONS_PATCH.md               ← Changes to make to existing operational docs
├── phases/
│   ├── phase-0-foundation/
│   │   ├── PRD-01-COMPONENTS.md      ← Component library expansion
│   │   └── PRD-02-DATA-LAYER.md      ← Hooks, types, state patterns
│   ├── phase-1-forms/
│   │   └── PRD-03-FORMS.md           ← Form system + validation
│   ├── phase-2-gp01/
│   │   └── PRD-04-GP01.md            ← GP-01 workflow complete rebuild
│   ├── phase-3-pages/
│   │   └── PRD-05-PAGES.md           ← Every remaining page
│   └── phase-4-polish/
│       ├── PRD-06-A11Y.md            ← Accessibility compliance
│       └── PRD-07-PERF.md            ← Performance + code quality
├── reference/
│   ├── component-specs.md            ← Exact component API contracts
│   ├── hook-specs.md                 ← Exact hook signatures + behavior
│   ├── schema-specs.md               ← Zod schema definitions
│   └── css-additions.md              ← CSS to append to globals.css
└── audit/
    └── current-issues.md             ← Per-file issue inventory
```

---

## Execution Order

**CRITICAL: Phases are sequential. Do not skip ahead.**

### Phase 0 — Foundation (PRD-01 + PRD-02)

**Goal:** Build the pri

*[truncated — see source for full prompt]*