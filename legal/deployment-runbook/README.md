# DEPLOYMENT RUNBOOK

> This runbook defines baseline production operations for LIC Legal Suite:

- deployment and migration flow
- startup readiness checks
- rollback proced

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment Runbook + Operational SLOs

This runbook defines baseline production operations for LIC Legal Suite:

- deployment and migration flow
- startup readiness checks
- rollback procedure
- incident response process
- baseline SLOs and operational metrics

## 1) Scope and Environments

- Services:
  - `apps/api` (NestJS + Prisma + queues)
  - `apps/web` (Next.js)
  - Postgres (`pgvector`), Redis, MinIO, optional ClamAV
- Expected deployment tiers:
  - `staging` (pre-prod validation)
  - `production` (customer traffic)

## 2) Pre-Deployment Checklist

Run from clean branch/commit intended for release:

```bash
pnpm install
pnpm test
pnpm build
```

Validate env configuration:

- API secrets (`SESSION_SECRET`, provider keys, encryption keys) are present.
- `INTEGRATION_TOKEN_ENCRYPTION_KEYS` + `INTEGRATION_TOKEN_ACTIVE_KEY_ID` are set.
- Storage/database/cache endpoints resolve.
- Optional scanners/providers are configured per policy.
- For `staging` and `production`, run provider-live readiness matrix before deploy:

```bash
pnpm test:provider-live
pnpm test:integrations-live
pnpm ops:drill:backup-restore -- --out-dir artifacts/ops
```

## 3) Deployment Procedure

1. Deploy infrastructure changes (if any) first.
2. Deploy API + web artifact for target commit.
3. Run Prisma migration on API runtime:

```bash
pnpm --filter api prisma:deploy
```

4. If required for environment bootstrap only, run seed (never on live customer DB):

```bash
pnpm --filter api prisma:seed
```

5. Start/restart app services.
6. Run readiness checks (below) before opening traffic.

## 4) Startup Readiness Checks

Required checks after rollout:

```bash
curl -fsS http://<api-host>/health
curl -fsS http://<web-host>/login
```

Operational readiness checklist:

- API process is serving `/health` without error.
- web app serves core route(s) and can reach API base URL.
- migration status is current (`prisma:deploy` succeeded).
- queue workers and Redis connectivity are healthy.
- document 

*[truncated — see source for full prompt]*