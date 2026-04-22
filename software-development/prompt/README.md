# Prompt

> **Goal:**
Develop a modular, extensible Cloudflare Worker that proxies all GitHub REST and GraphQL endpoints, exposes validated Hono routes, and dynam

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🧠 AI Builder Prompt — Cloudflare Worker GitHub Proxy

**Goal:**
Develop a modular, extensible Cloudflare Worker that proxies all GitHub REST and GraphQL endpoints, exposes validated Hono routes, and dynamically generates OpenAPI specs for agent discovery.

---

## 1️⃣ Core Objectives

- Implement **Hono** + **@hono/zod-openapi** for routing + schema-driven validation
- Use **Octokit** clients for REST and GraphQL operations
- Generate `/openapi.json` and `/openapi.yaml` dynamically
- Structure the code to be **agent-friendly**, **modular**, and **self-documenting**
- Provide end-to-end testable routes for:
- `/api/octokit/rest/...`
- `/api/octokit/graphql/...`
- `/api/tools/files/...`
- `/api/tools/prs/...`

---

## 2️⃣ Folder Structure

````

/src
/octokit
core.ts
/rest
repos.ts
contents.ts
issues.ts
pulls.ts
/graphql
graphql.ts
index.ts
/tools
files.ts
prs.ts
issues.ts
/utils
base64.ts
paginate.ts
etagCache.ts
rateLimit.ts
hono.ts
index.ts
/docs
AGENTS.md
prompt.md
wrangler.toml
README.md
package.json

````

---

## 3️⃣ Build Requirements

- ✅ TypeScript + ESM modules
- ✅ Hono framework
- ✅ @hono/zod-openapi for schema validation
- ✅ @octokit/rest & @octokit/graphql for GitHub API
- ✅ Zod for runtime safety
- ✅ `wrangler.toml` configured for Cloudflare deployment

---

## 4️⃣ Functional Highlights

- Proxy GitHub REST calls under `/api/octokit/rest/:namespace/:method`
- Proxy GitHub GraphQL calls under `/api/octokit/graphql`
- Abstract common workflows (files, PRs, issues) under `/api/tools/...`
- Implement base64-safe file upsert logic (`mode: text|binary|auto`)
- Add ETag KV caching and rate-limit retry handling
- Log every inbound and outbound call with structured metadata

---

## 5️⃣ OpenAPI Integration

Use `@hono/zod-openapi` to:

- Derive OpenAPI specs from Zod schemas
- Serve `/openapi.json` (JSON) and `/openapi.yaml` (YAML)
- Attach examples and endpoint descriptions
- Mark `/api/tools/*` endpoints with `x-agent: true` metadata for GPT discovery

---


*[truncated — see source for full prompt]*