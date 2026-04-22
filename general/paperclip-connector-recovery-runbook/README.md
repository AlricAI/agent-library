# Paperclip Connector Recovery Runbook

> Use this runbook when Blueprint Paperclip automation degrades because GitHub webhook/plugin configuration or Google Calendar server-side configuration is incomplete.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Paperclip Runtime Recovery Runbook

Use this runbook when Blueprint Paperclip automation degrades because GitHub webhook/plugin configuration or Google Calendar server-side configuration is incomplete.

This is a connector-recovery runbook, not the full autonomous-alpha launch checklist. For the public launch decision, run the full gate sequence in [autonomous-org-launch-checklist.md](/Users/nijelhunt_1/workspace/Blueprint-WebApp/docs/autonomous-org-launch-checklist.md).

## What This Runbook Covers

- shared Paperclip health and plugin readiness
- GitHub webhook/plugin prerequisite checks
- Google Calendar server-side configuration for field-ops booking/reschedule automation
- targeted post-fix verification for repo/CI access and field-ops calendar usage

This runbook is intentionally explicit about what is machine-verifiable versus what still requires operator-owned service configuration.

## 1. Verify Shared Paperclip Health

Run:

```bash
scripts/paperclip/verify-blueprint-paperclip.sh
```

Expected:

- the shared Paperclip instance is reachable on the canonical local API URL
- the Blueprint automation plugin is `ready`
- required routines are present
- GitHub prerequisite env vars are present:
  - `BLUEPRINT_PAPERCLIP_GITHUB_OWNER`
  - `BLUEPRINT_PAPERCLIP_GITHUB_TOKEN`
  - `BLUEPRINT_PAPERCLIP_GITHUB_WEBHOOK_SECRET`

If this step fails on missing GitHub env/config, treat it as a connector/auth configuration problem, not generic runtime instability.

Before continuing, also run:

```bash
npm run alpha:preflight
npm run smoke:agent
```

Reason:

- `verify-blueprint-paperclip.sh` proves Paperclip/package health
- `alpha:preflight` proves the production env contract is actually present
- `smoke:agent` proves the selected structured runtime provider is live

Do not treat a passing Paperclip verify alone as public-launch readiness.

## 2. Refresh Plugin Configuration

Run:

```bash
scripts/paperclip/configure-blueprint-paperclip-plugin.sh
scripts/paperclip/setup-g

*[truncated — see source for full prompt]*