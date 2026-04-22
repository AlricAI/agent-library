# Anvil Loop Guardrails

> > Last updated: April 20, 2026
> Applies to: every issue dispatched through the Mini factory
> Enforced by: Sim-Iterate Orchestrator (FORGE-266) + CEO

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Anvil Loop Guardrails

> Last updated: April 20, 2026
> Applies to: every issue dispatched through the Mini factory
> Enforced by: Sim-Iterate Orchestrator (FORGE-266) + CEO manual monitor until orchestrator is live

---

## Goal

Make every Anvil Loop iteration **time-bounded, cost-bounded, and escalation-aware** so no loop runs silently for hours burning tokens. Every issue either ships or kicks to the CEO with a clear reason — no middle state.

## The three caps (HARD)

| Cap | Value | Measured on |
|---|---|---|
| **Iterations** | 5 strikes max | count of `forge.runs` linked to the issue with `status in ('succeeded','failed')` |
| **Wall-clock** | 90 minutes total | `now() - min(started_at)` across all runs on the issue |
| **Cost** | $8 USD | `sum(cost_usd)` across all runs on the issue |

First cap to trigger → immediate escalation. No "just one more try."

## Extra escalation triggers

1. **3 consecutive same-mode failures** — same error class 3 runs in a row (e.g., 3x build failure on same symbol). Pattern = blocker, not flake.
2. **Agent posts `escalate-to-ceo`** — any agent comment containing that literal tag escalates immediately.
3. **Agent posts `agent-report: needs-human`** — legacy tag, also escalates.
4. **Manual halt** — `forge.ship_loop_state.halted = true` (when the table exists — tracked as FORGE-TBD).

## Escalation action (atomic)

When any trigger fires:

1. Cancel all `queued` + `running` runs for this issue (SQL: `update forge.runs set status='cancelled', error='guardrail: <trigger>' where agent_id in (...) and status in ('queued','running')`)
2. Update the issue: `status='blocked'`, append a comment prefixed `[ESCALATE]` with:
   - Which cap triggered + value at trigger time
   - Link to the last 3 runs (ids)
   - Last error from each run
   - Proposed next action (CEO guidance needed)
3. Write to `forge.ship_loop_state` halt log (if table exists)
4. (Optional) Push notification to CEO via Supabase realtime — TBD infrastructure

##

*[truncated — see source for full prompt]*