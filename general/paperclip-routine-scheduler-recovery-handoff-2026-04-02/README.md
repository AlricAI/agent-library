# Paperclip Routine Scheduler Recovery Handoff 2026 04 02

> Use the prompt below as the starting instruction set for the next repair session.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Paperclip Routine Scheduler Recovery Handoff

Use the prompt below as the starting instruction set for the next repair session.

## Master Prompt

You are continuing the in-progress Blueprint Paperclip scheduler recovery.

Workspace:
- Repo: `/Users/nijelhunt_1/workspace/Blueprint-WebApp`
- Related local Paperclip repo: `/Users/nijelhunt_1/workspace/paperclip`
- Paperclip home: `/Users/nijelhunt_1/workspace/.paperclip-blueprint`
- Env file: `/Users/nijelhunt_1/workspace/.paperclip-blueprint.env`
- Timezone context: `America/New_York`
- Production VPS inventory:
  - host label: `paperclip-prod-01`
  - provider: DigitalOcean Droplet
  - public IPv4: `206.81.11.69`
  - private IPv4: `10.116.0.2`
  - region: `NYC1`
  - size: `4 GB / 80 GB Disk / Ubuntu 24.04 (LTS) x64`
  - VPC: `default-nyc1`
  - VPC CIDR: `10.116.0.0/20`
  - current firewall state reported by operator: no DigitalOcean firewall attached

Read first:
1. `/Users/nijelhunt_1/workspace/Blueprint-WebApp/PLATFORM_CONTEXT.md`
2. `/Users/nijelhunt_1/workspace/Blueprint-WebApp/WORLD_MODEL_STRATEGY_CONTEXT.md`
3. `/Users/nijelhunt_1/workspace/Blueprint-WebApp/DEPLOYMENT.md`
4. `/Users/nijelhunt_1/workspace/Blueprint-WebApp/package.json`

Mission:
Finish the last two Paperclip scheduler recovery problems and leave both local and production host context cleanly documented:

1. Confirm that a scheduled routine now propagates all the way from `routine_triggers` and `routine_runs` into a brand-new `heartbeat_runs` row for its target agent.
2. Identify and remove the extra Paperclip server process tree serving `127.0.0.1:3101` while preserving the healthy primary instance on `127.0.0.1:3100`.

Hard requirements:
- Do not use destructive git commands.
- Do not revert unrelated user changes.
- Use `apply_patch` for file edits.
- Keep checked-in cron values from `.paperclip.yaml`.
- Prefer repo scripts and Paperclip APIs over ad hoc DB mutation, but use surgical direct DB access when the API path is too slow or overload

*[truncated — see source for full prompt]*