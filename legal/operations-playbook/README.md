# OPERATIONS PLAYBOOK

> This is the canonical operations manual for LIC Legal Suite collaboration.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Operations Playbook

This is the canonical operations manual for LIC Legal Suite collaboration.

If any procedural guidance conflicts with other docs, this file wins.

## 1) Collaboration Model

### Symphony Service

Owns issue polling and execution orchestration.

Responsibilities:
1. Poll Linear and select eligible issues from configured execution states.
2. Create isolated per-issue workspaces.
3. Run coding-agent sessions using repository `WORKFLOW.md`.
4. Produce run outputs and structured run reports for review.

Restrictions:
1. Symphony is execution orchestration, not backlog governance.
2. Linear canonical status/evidence discipline is still enforced by local operators.
3. Only assigned issues in `Ready` (and active execution states) are eligible for pickup.

### Local Operator

Responsibilities:
1. Maintain `WORKFLOW.md` policy and environment wiring.
2. Review Symphony outputs, open/merge PRs, and resolve conflicts.
3. Maintain Linear state/evidence as source of truth.
4. Run housekeeping/sync commands after merges.

Restrictions:
1. Do not bypass Symphony workflow policy for issue execution unless incident response requires manual override.
2. Do not treat GitHub mirror state as canonical backlog state.
3. Only the coordinator moves issues to `Ready` and assigns them for execution.

## 2) Start-of-Session Preflight

Run before planning/coding in any chat or starting Symphony:

```bash
pnpm ops:preflight
```

`ops:preflight` checks:
1. Branch + dirty tree summary.
2. Canonical control file drift:
   - `tools/backlog-sync/requirements.matrix.json`
   - `tools/backlog-sync/session.snapshot.json`
   - `docs/SESSION_HANDOFF.md`
   - `docs/WORKING_CONTRACT.md`
   - `README.md`
3. Required token presence (names only, never values).
4. `pnpm backlog:verify` pass/fail.
5. `pnpm backlog:matrix:check` (only if verify succeeds).
6. `pnpm backlog:handoff:check` pass/fail.
7. Artifact output to `artifacts/ops/operator-preflight.json`.
8. (Manual) confirm Symphony ru

*[truncated — see source for full prompt]*