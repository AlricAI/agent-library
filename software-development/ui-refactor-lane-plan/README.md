# UI REFACTOR LANE PLAN

> ## Canonical Source + Conflict Rule

- Canonical precedence: `docs/UI_CANONICAL_PRECEDENCE.md`.
- Product app scope uses LIC design-system references 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# KAR-54 UI/UX Refactor Lane Plan (LIC Canonical)

## Canonical Source + Conflict Rule

- Canonical precedence: `docs/UI_CANONICAL_PRECEDENCE.md`.
- Product app scope uses LIC design-system references only; `lic-design-system/references/marketing-site.md` is excluded.
- If local legacy docs/components conflict, canonical precedence wins.

## Why This Lane Exists

UI work is currently split across legacy styling decisions and partially migrated LIC conventions. This lane standardizes the app as a procedural operations system and creates missing PRD/screen definitions required for existing and backlog functionality.

## Deliverables

1. Canonical token and interaction lock.
2. App shell + primitive compliance under LIC rules.
3. PRD and screen-spec coverage for existing routes.
4. Blocked PRD/screen placeholders for backlog features that are not yet designed.
5. Regression and rollout gates that prevent reintroduction of non-compliant styles.

## Phased Execution

### Phase 0: Canonical lock + guardrails

- Publish and ratify conflict-resolution contract.
- Add automated style guard checks (`pnpm ui:contract:check`).
- Wire guardrails into UI rollout CI workflow.
- Update token contract and checklist references.
- Enforce standards-manual boundary: extract standards from manual sections, but do not copy manual-app shell/nav/metadata UX into product routes.

### Phase 1: Product PRD + screen inventory (existing functionality)

Create PRD + screen specs for these routes:
- `apps/web/app/dashboard/page.tsx`
- `apps/web/app/matters/page.tsx`
- `apps/web/app/matters/[id]/page.tsx`
- `apps/web/app/contacts/page.tsx`
- `apps/web/app/communications/page.tsx`
- `apps/web/app/documents/page.tsx`
- `apps/web/app/billing/page.tsx`
- `apps/web/app/portal/page.tsx`
- `apps/web/app/ai/page.tsx`
- `apps/web/app/imports/page.tsx`
- `apps/web/app/exports/page.tsx`
- `apps/web/app/reporting/page.tsx`
- `apps/web/app/admin/page.tsx`
- `apps/web/app/login/page.tsx`
- `apps/web/app/shared-

*[truncated — see source for full prompt]*