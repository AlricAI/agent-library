# Tracker

> Items discovered during execution that need attention but don't belong in the product backlog.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Engineering Tracker

Items discovered during execution that need attention but don't belong in the product backlog.
Project-Manager reads this at the start of every session. Items graduate to stories (`doc/stories/`), bugs (`doc/bugs/`), or RFCs (`doc/rfc/`) when clarified.

Last updated: 19 April 2026 — resolved T-011 after HT-082 follow-up closeout.

## Open

| ID | Source | Category | Description | Blocked By | Priority | Age (pipelines) |
|---|---|---|---|---|---|---|
| T-002 | HT-052 pipeline | tech-debt | 4 test_auth.py::TestLogin tests fail — passlib bcrypt backend: `module 'bcrypt' has no attribute '__about__'`. Likely bcrypt 4.x + passlib incompatibility. Fix: pin bcrypt<4.1 or migrate to bcrypt directly. | — | MEDIUM | 0 |
| T-005 | HT-031 code-review residual | tech-debt | `src/ui/pages/inventory_page_controller.py` remains high-complexity at 379 lines after cap fix. Schedule targeted decomposition of orchestration methods before next bulk-feature expansion. | — | MEDIUM | 0 |
| T-006 | BUG-HUNT-14-04-26.1 | test-gap | Add a real Postgres concurrent import contention integration test to validate ordered DELETE clear-path behavior under lock pressure; current BUG-001 proof is unit-level only. | — | MEDIUM | 0 |
| T-009 | HT-050 browser validation | follow-up | In browser validation, `HT_READONLY` sometimes flips back to `true` shortly after entering edit mode, likely due to a canvas re-init/personal-draft load race. It did not block the final production-path resize fix, but it is worth a separate targeted investigation because it can interfere with tooling/devtools sessions. | — | LOW | 0 |
|---|---|---|---|---|---|---|

## Resolved

| ID | Resolution | Resolved Via | Date |
|---|---|---|---|
| T-001 | Completed HT-051 follow-up by wiring remove-from-view actions into the shared HT-032 undo stack with local snapshot restore/removal behavior and matching test coverage. | HT-032 canvas undo/redo implementation | 14 Apr 2026 |
| T-003 | Hardened destructive

*[truncated — see source for full prompt]*