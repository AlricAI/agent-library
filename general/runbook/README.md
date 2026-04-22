# RUNBOOK

> This is the operator's playbook for Magic Indexer (the
`hb-agent/magic-indexer` fork of `hypercerts-org/hyperindex`,
deployed as the `magic-indexer` R

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Magic Indexer Operations Runbook

This is the operator's playbook for Magic Indexer (the
`hb-agent/magic-indexer` fork of `hypercerts-org/hyperindex`,
deployed as the `magic-indexer` Railway service in the `dev`
environment).

If you're a new contributor or a fresh AI session opening this
repo, **read [AGENTS.md](../AGENTS.md) first** for the dev
guide and project layout, then come back here for deployment
and operations.

---

## Live environment

| Item                | Value                                              |
|---------------------|----------------------------------------------------|
| Public URL          | https://magic-indexer-dev.up.railway.app           |
| GraphQL (public)    | https://magic-indexer-dev.up.railway.app/graphql   |
| GraphQL (admin)     | https://magic-indexer-dev.up.railway.app/admin/graphql |
| GraphiQL playground | https://magic-indexer-dev.up.railway.app/graphiql  |
| Health              | https://magic-indexer-dev.up.railway.app/health    |
| Stats               | https://magic-indexer-dev.up.railway.app/stats     |
| Metrics             | https://magic-indexer-dev.up.railway.app/metrics   |
| Railway dashboard   | https://railway.com/project/7d6c4e52-de61-439f-96c0-3ded4114b9be |
| GitHub repo         | https://github.com/hb-agent/magic-indexer          |
| Active branch       | `per-labeler-definitions`                          |
| Backing database    | Postgres 18 (Railway-managed, in same project)     |

**Secrets** (`SECRET_KEY_BASE`, `ADMIN_API_KEY`) live in:
1. The Railway dashboard → `magic-indexer` service → Variables tab
2. The operator's password manager (1Password / Bitwarden / Vault)

They are **not** in this repository, in `.env.example`, or in
any committed file. If you lose them and need to rotate, see
[Rotating secrets](#rotating-secrets) below.

---

## Build, test, lint (local development)

From a clean checkout:

```bash
git checkout per-labeler-definitions
make setup           # generates .env with a fr

*[truncated — see source for full prompt]*