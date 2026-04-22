# AI PIPELINE PLAN

> ## Context
The app has a working auth flow, UI shell (tabs, settings, debug), and state management (Zustand + MMKV + TanStack Query). There is NO data

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MyMemory AI Pipeline — 4-Phase Implementation Plan

## Context
The app has a working auth flow, UI shell (tabs, settings, debug), and state management (Zustand + MMKV + TanStack Query). There is NO database schema, NO server/API layer, and NO AI integration. This plan adds AI-powered ingest/digest pipelines using Vercel AI SDK v6 + OpenAI via Expo API Routes, with Drizzle ORM for Supabase Postgres.

**Architecture decisions (confirmed):**
- Server: Expo API Routes (`app/api/...+api.ts`) → EAS Hosting (Cloudflare Workers)
- AI: OpenAI GPT-4o-mini via `@ai-sdk/openai`
- DB: Supabase Postgres + pgvector, adjacency list + junction tables
- Types: Zod schemas as single source of truth, types inferred (never hand-written)

---

## Phase 1: AI SDK + DB Foundation

### 1.1 Install dependencies
```
pnpm add ai @ai-sdk/openai zod drizzle-orm postgres
pnpm add -D drizzle-kit
```

### 1.2 Config changes
- `app.json` line 24: `"output": "static"` → `"output": "server"` (required for API routes)
- `.env` — add server-side vars: `OPENAI_API_KEY`, `SUPABASE_SERVICE_ROLE_KEY`, `DATABASE_URL`, `JINA_API_KEY`
- `.env.example` — document new vars
- New `drizzle.config.ts` at root (schema: `./src/db/schema/*.ts`, out: `./src/db/migrations`)

### 1.3 Database schema (Drizzle + Zod)

Each file exports: Drizzle table, Zod insert/select schemas, inferred types.

| File | Tables |
|------|--------|
| `src/db/schema/enums.ts` | pgEnum definitions + Zod enum schemas |
| `src/db/schema/entries.ts` | `entries` |
| `src/db/schema/tags.ts` | `tags`, `entryTags` |
| `src/db/schema/topics.ts` | `topics`, `entryTopics` |
| `src/db/schema/spaces.ts` | `spaces`, `entrySpaces`, `spaceRelations` (NEW) |
| `src/db/schema/entry-notes.ts` | `entryNotes` |
| `src/db/schema/embeddings.ts` | `embeddings` (pgvector via `customType`) |
| `src/db/schema/digests.ts` | `digests`, `digestEntries` |
| `src/db/schema/space-suggestions.ts` | `spaceSuggestions` |
| `src/db/schema/cron-configs.ts` | `cronConfigs` |
| `

*[truncated — see source for full prompt]*