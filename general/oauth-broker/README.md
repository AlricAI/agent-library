# Oauth Broker

> Language: [English](oauth-broker.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Optional GitHub OAuth Broker

Language: [English](oauth-broker.md) | [简体中文](oauth-broker.zh-CN.md)

Use this only to simplify GitHub OAuth login UX. It is not in memory sync data path.

## Minimum Steps (Recommended)

1. Deploy broker (one-click link or CLI).
2. Copy broker URL (for example: `https://xxx.workers.dev`).
3. In WebUI `Configuration`:
   - set `OAuth Broker URL`
   - click `Sign In via GitHub`

Sync still runs locally via Git on user machine.

Health check (replace `<BROKER_URL>`):

```bash
curl -sS -X POST "<BROKER_URL>/v1/github/device/start" \
  -H 'Content-Type: application/json' \
  -d '{}' | jq .
```

Expected: JSON error like `missing client_id` (endpoint reachable).

## One-Click Deploy Entry Points

- Cloudflare Worker:
  - `https://deploy.workers.cloudflare.com/?url=https://github.com/NoPKT/omnimem/tree/main/examples/oauth-broker/cloudflare-worker`
  - If Cloudflare shows a generic monorepo warning page, continue; this template includes `wrangler.toml`.
- Vercel:
  - `https://vercel.com/new/clone?repository-url=https://github.com/NoPKT/omnimem&root-directory=examples%2Foauth-broker%2Fvercel&project-name=omnimem-oauth-broker`
- Railway:
  - `https://railway.app/new/template?template=https://github.com/NoPKT/omnimem/tree/main/examples/oauth-broker/railway`
- Fly.io template reference:
  - `https://github.com/NoPKT/omnimem/tree/main/examples/oauth-broker/fly`

## What To Fill On Deploy Pages

- Common required value:
  - `GITHUB_OAUTH_CLIENT_ID` (GitHub OAuth App client id)
- Cloudflare Worker:
  - In Worker Settings -> Variables and Secrets, set `GITHUB_OAUTH_CLIENT_ID`.
- Vercel:
  - In Project Settings -> Environment Variables, add `GITHUB_OAUTH_CLIENT_ID` (Production at minimum).
- Railway:
  - In Variables tab, add `GITHUB_OAUTH_CLIENT_ID`.
- Fly.io:
  - App name can be arbitrary unique name.
  - Set secret with `fly secrets set GITHUB_OAUTH_CLIENT_ID=...`.

## CLI Fallback (Deterministic)

```bash
# readiness check
omnimem oauth-broker do

*[truncated — see source for full prompt]*