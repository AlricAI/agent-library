# Decisions

> **Last Updated**: 2026-04-01T12:35:00-04:00

Every architectural decision is recorded here so no future session re-debates it.

Current reading rule:


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DECISIONS LOG — WHY WE DID WHAT WE DID

**Last Updated**: 2026-04-01T12:35:00-04:00

Every architectural decision is recorded here so no future session re-debates it.

Current reading rule:

- Read the newest entries first.
- If an older entry conflicts with the March 31, 2026 doctrine correction, treat the older entry as historical context only.

---

## 2026-03-31: Prelaunch doctrine correction for LLC-controlled revenue

**Decision**: Treat current LLC-controlled revenue under a founder-directed conservative `10% charitable cap` and treat historical `60/30/10`, `100% charity`, and `100% DAO` language as legacy unless canonical docs explicitly restore it.
**Why**: Close to launch, Josh forced a conservative doctrine correction to avoid unsupported tax exposure and to stop older mission language from being mistaken for current operating truth.
**Impact**: Canonical memory, sync prompts, ClawX repo docs, MCP protocol metadata, and app impact labeling were updated. Historical chain artifacts remain documented as history, not automatic current doctrine.
**Status**: Active

---

## 2026-03-10: Payment truth must be verified from live repo files, not archaeology

**Decision**: Treat live payment truth as whatever is currently implemented in `C:\ANTIGRAVITY` under the backend payment files, frontend payment links, and the canonical payment briefing, and treat old PR email archaeology or export folders as recovery-only unless re-verified.
**Why**: Payment questions were drifting between old Stripe-era comments, dormant Paymentwall exports, and newer Square code. That is exactly the kind of memory loss that creates false architectural pivots.
**Impact**: `briefings/LIVE-PAYMENT-SOURCE-OF-TRUTH.md` is now the first stop for payment questions. Future sessions should verify `verify.py`, `webhooks.py`, `config.py`, `health.py`, `App.tsx`, and `square_catalog.json` before accepting any historical claim.
**Status**: Active

## 2026-03-10: Square merchant-settings evidence outr

*[truncated — see source for full prompt]*