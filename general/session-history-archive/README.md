# SESSION HISTORY ARCHIVE

> This archive stores prior long-form handoff history moved out of `docs/SESSION_HANDOFF.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Session History Archive

This archive stores prior long-form handoff history moved out of `docs/SESSION_HANDOFF.md` during ops docs reorg.

## Archived Snapshot

# LIC Legal Suite Session Handoff

This document is the persistent handoff layer for new chats. Linear is canonical; this file provides the minimal runbook to reconstruct context quickly and consistently.

## Snapshot Metadata

- Snapshot File: `tools/backlog-sync/session.snapshot.json`
- Snapshot Timestamp: `2026-02-27T01:50:06.383Z`
- Snapshot Schema Version: `1.1.0`
- Last Successful Mirror Verify: `2026-02-26T23:55:51.297Z`

## Canonical Context Routing (Linear-First)

Use this order when reconstructing context:

1. Active Linear issue (`In Progress`/`In Review`)
2. Linear project status for parity scope
3. `tools/backlog-sync/requirements.matrix.json`
4. `README.md` -> `New Chat Bootstrap`
5. `Prompt-Context`
6. `docs/PROMPT_CANONICAL_SOURCES.md`

Rule: GitHub issues are mirror-only for parity scope and never source-of-truth for task status.

## Runtime Identity

- Monorepo: `apps/api` (NestJS + Prisma + BullMQ), `apps/web` (Next.js App Router), `docker-compose.yml` (Postgres pgvector, Redis, MinIO, optional ClamAV)
- Canonical backlog model: Linear project `Prompt Parity - LIC Legal Suite`
- Sync model: one-way Linear -> GitHub mirror via `tools/backlog-sync/linear_to_github.mjs`

## New Chat Bootstrap (Command-First)

Run these in order:

```bash
git status --short --branch
pnpm backlog:verify
pnpm backlog:matrix:check
pnpm backlog:snapshot
```

Then read:

1. `tools/backlog-sync/session.snapshot.json`
2. `docs/SESSION_HANDOFF.md`
3. Top priority Linear issues listed in snapshot (`priority.topRequirements`, `linearSummary.inProgressIssueKeys`)

## Priority Lane Policy

Selection policy:

1. `phase-1` requirements before `phase-2`
2. Within a phase: `Missing` requirements before `Partial`
3. Within same phase/status: `High` risk before `Medium` before `Low`
4. Security/data-integrity/portability bef

*[truncated — see source for full prompt]*