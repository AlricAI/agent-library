# DEPLOYMENT

> This guide covers deploying the Multi-Protocol GitHub Worker with all its features including Durable Objects, WebSockets, and MCP support.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment Guide - Multi-Protocol GitHub Worker

This guide covers deploying the Multi-Protocol GitHub Worker with all its features including Durable Objects, WebSockets, and MCP support.

## Prerequisites

- Cloudflare account with Workers enabled
- wrangler CLI installed (`npm install -g wrangler`)
- GitHub Personal Access Token (for GitHub API operations)
- Worker API key (for authentication)

---

## 🚨 IMPORTANT: Durable Object Migrations

**This Worker includes Durable Object migrations and MUST be deployed using `wrangler deploy` for the first time.**

### Why?

The Worker includes a new Durable Object class (`RoomDO`) with a migration defined in `wrangler.jsonc`:

```jsonc
{
  "migrations": [
    {
      "tag": "v1",
      "new_sqlite_classes": ["OrchestratorAgent", "RetrofitAgent"]
    },
    {
      "tag": "v2",
      "new_classes": ["RoomDO"]
    }
  ]
}
```

**Cloudflare requires migrations to be fully applied using `wrangler deploy` before you can use gradual deployments (`wrangler versions upload`).**

### Deployment Command

```bash
# First deployment (or when adding new Durable Objects)
npx wrangler deploy

# Subsequent deployments (after migration is complete)
npx wrangler versions upload  # Only after migration is live
```

### Error You Might See

If you try to use `wrangler versions upload` before deploying the migration:

```
Version upload failed. You attempted to upload a version of a Worker that includes
a Durable Object migration, but migrations must be fully applied by running
"wrangler deploy".
```

**Solution:** Run `npx wrangler deploy` instead.

---

## Step-by-Step Deployment

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Secrets

Set your secrets using wrangler:

```bash
# GitHub Personal Access Token
npx wrangler secret put GITHUB_TOKEN

# Worker API Key (for protecting API endpoints)
npx wrangler secret put WORKER_API_KEY
```

### 3. Review Configuration

Check `wrangler.jsonc` to ensure all bindings are c

*[truncated — see source for full prompt]*