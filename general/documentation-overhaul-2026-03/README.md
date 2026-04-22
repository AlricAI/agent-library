# DOCUMENTATION OVERHAUL 2026 03

> **Later consolidation (scan):** Remaining drifting docs moved into `docs/`: `frontend/admin/docs/navigation-patterns-catalog.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Documentation Overhaul — Phase 6 Deliverables (2026-03)

**Later consolidation (scan):** Remaining drifting docs moved into `docs/`: `frontend/admin/docs/navigation-patterns-catalog.md` → `docs/frontend/navigation-patterns-catalog.md`; `frontend/miniapp/LAYOUT-ARCHITECTURE.md` → `docs/frontend/miniapp-layout-architecture.md`; `bot/docs/RELEASE.md`, `PRODUCTION_PLAN.md`, `BOT_MENU_ARCHITECTURE.md` → `docs/bot/release.md`, `production-plan.md`, `bot-menu-architecture.md`. Redirect READMEs left in `frontend/admin/docs/`, `bot/docs/`, and `frontend/miniapp/README.md` added.

## 1. Audit Summary

Disposition key: **KEEP** = current, essential; **UPDATE** = refresh links/version/format; **MERGE** = consolidated into another doc; **LEGACY/REDUNDANT/DELETE** = removed or archived.

| Path | Disposition |
|------|-------------|
| README.md | UPDATE (rewritten) |
| CHANGELOG.md | UPDATE (Keep a Changelog) |
| CONTRIBUTING.md | KEEP |
| AGENTS.MD | KEEP |
| docs/README.md | UPDATE |
| docs/guides/*.md | KEEP |
| docs/consolidation-plan.md | UPDATE |
| docs/backlog/*.md | KEEP / UPDATE |
| docs/api/*.md | KEEP / UPDATE (OpenAPI path) |
| docs/ops/*.md | KEEP |
| docs/observability/*.md | KEEP / UPDATE / MERGE (see merge log) |
| docs/security/*.md | KEEP |
| docs/specs/*.md | KEEP |
| docs/release/*.md | KEEP (dated one-offs deleted) |
| docs/audits/*.md | KEEP |
| docs/frontend/**/*.md | KEEP / UPDATE |
| docs/codebase-map.md | KEEP (SYSTEM_MAP merged in) |
| docs/design-system/ORBITAL_GRADE.md | MERGE → frontend/design/design-system.md |
| docs/BASELINE.md, ROADMAP.md, etc. | DELETE (see deletion log) |

Full audit tables: see plan at `.cursor/plans/documentation_consolidation_overhaul_*.plan.md` (sections 1.1–1.10).

---

## 2. Deletion Log

| File | Rationale |
|------|-----------|
| docs/ROADMAP.md | Remove roadmap per prompt; use GitHub Projects |
| docs/release/pre-release-review-2026-02-28.md | Dated one-off; content folded into release checklist / runbook |
| docs/re

*[truncated — see source for full prompt]*