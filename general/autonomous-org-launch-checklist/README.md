# Autonomous Org Launch Checklist

> Last audited: 2026-04-12

This checklist is the execution-order runbook for deciding whether Blueprint's Hermes/Paperclip autonomous organization is r

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Autonomous Org Launch Checklist

Last audited: 2026-04-12

This checklist is the execution-order runbook for deciding whether Blueprint's Hermes/Paperclip autonomous organization is ready for public alpha launch.

Use it in order. Do not skip ahead to Paperclip adapter checks and assume launch readiness if the product-side alpha gate is still failing.

## Launch Decision

### Internal launch

Good enough when all of these are true:

- `npm run alpha:check` passes
- local Paperclip company + plugin + routines verify
- the team understands which lanes remain permanently human-gated

### Public autonomous alpha launch

Good enough only when all of these are true:

- every internal-launch item passes
- `npm run alpha:preflight` passes with no required failures
- `npm run smoke:agent` passes
- `scripts/paperclip/verify-blueprint-paperclip.sh --smoke` passes
- GitHub webhook/plugin config and server-side Google Calendar wiring are complete
- paid buyer flows, ops notifications, and production automation lanes are backed by real credentials, not local fallbacks

## Current Status

Observed on 2026-04-12:

- Completed: targeted city-launch and autonomy verification
  Result: city-launch planning and execution harnesses, autonomy scheduler, autonomous outbound, and creative factory tests are passing in-repo.
- Completed: `npm run check`
  Result: passing.
- Completed: `npm run smoke:agent`
  Result: passed locally against `codex_local` with `gpt-5.4-mini`.
- Completed with waivers: `npm run alpha:preflight`
  Result: passes in `local_test` mode, but only because Stripe and research-outbound requirements are waived in this workspace.
- Completed: generic city launcher architecture
  Result: the WebApp now supports generic city launch packet generation, Paperclip issue-tree dispatch, machine-readable budget policy, and canonical city ledgers for prospects, buyer targets, first touches, and spend.
- Still blocked for public autonomous alpha: production credentials, connectors

*[truncated — see source for full prompt]*