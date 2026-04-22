# Mcm Forge Orchestrator Plan

> **Date:** 2026-04-03
**Status:** Draft
**Author:** COO + Claude Code

---

## 1. Executive Summary

MCM Forge Orchestrator replaces Paperclip as our a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCM Forge Orchestrator -- Project Plan

**Date:** 2026-04-03
**Status:** Draft
**Author:** COO + Claude Code

---

## 1. Executive Summary

MCM Forge Orchestrator replaces Paperclip as our agent orchestration layer. It is purpose-built for our stack: Supabase (Postgres + Realtime), Next.js on Vercel (dashboard), and a Mac Mini running a Node.js orchestrator process that spawns CLI agents (Claude, Gemini, Codex).

**Why build our own:**
- Paperclip bundles an embedded Postgres (PGlite), a Vite SPA, and an Express monolith. We already have Supabase and a Vercel-deployed Next.js app.
- Paperclip's plugin system, multi-tenant auth, billing, and embedded DB add complexity we don't need.
- We need first-class iOS simulator integration (visual QA loop) that Paperclip doesn't support.
- We need tight integration with our existing Supabase tables (companies, trail_systems, etc.).
- 46K stars means Paperclip moves fast and breaks things. Invisible issues (#2251), missing promptTemplate (#206), and hidden UI (#1423) cost us days.

**What we keep from Paperclip's design:**
- The heartbeat/wakeup/run lifecycle (proven pattern)
- CLI adapter architecture (spawn `claude -p`, `gemini -p`, `codex -p` as child processes)
- Session persistence (resume conversations across heartbeats)
- Git worktree isolation per task
- Issue board with single-assignee checkout semantics
- @-mention wakeups between agents
- Routine triggers with cron + catch-up policies
- Cost event ledger per agent per run
- Org hierarchy with `reportsTo` chains

**What we drop:**
- Embedded Postgres (use Supabase)
- Express API + Vite SPA (use Next.js API routes + React Server Components)
- Plugin system (YAGNI)
- Multi-tenant auth / sign-up flow (single-owner, Supabase auth)
- Better-Auth integration
- Company export/import
- Complex approval workflows (start with manual dashboard approval)
- Adapter marketplace (we support exactly 3 CLIs)

---

## 2. Architecture Overview

```
+---------------------+         +---

*[truncated — see source for full prompt]*