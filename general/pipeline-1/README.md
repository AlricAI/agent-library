# PIPELINE

> Current operations guide for the active local-first pipeline.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pipeline Guide

Current operations guide for the active local-first pipeline.

Use this doc for:
- the current command surface
- the current collection -> queue -> extraction -> review flow
- the current local UI and inspection surfaces
- the current artifact/storage boundaries

Use other docs for adjacent concerns:
- `docs/VISION_AND_ARCHITECTURE.md` for the durable north-star architecture
- `docs/ROADMAP.md` for what is next
- `docs/LISTING_SCHEMA.md` for the normalized listing contract
- `data/README.md` for on-disk layout details
- `src/ui/ARCHITECTURE.md` for dashboard/inspector contributor guidance

## Current Boundary

The active system boundary is:
- local SQLite is the canonical write-side
- raw artifacts stay on disk under `data/`
- collection runs against a live authenticated browser tab
- queue processing writes `processed_payloads` and `listing_records` into SQLite
- local operator surfaces read directly from SQLite

The hosted/public read path is not the active write-side. For the current intended Cloudflare split, see:
- `docs/reviews/2026-03-16_00-40-29_CLOUDFLARE_DEPLOYMENT_READINESS_REVIEW.md`

## Stage Map

1. collection
   - collect DOM posts from a Facebook group page
   - persist runs, observations, raw artifacts, and collected exports
2. processing queue
   - enqueue eligible observations
   - claim jobs atomically
   - process jobs into structured payloads and listing rows
3. evidence and resolution
   - enrich observations into reusable evidence fragments
   - resolve selected fields into layered effective values
4. local operator surfaces
   - inspect storage, jobs, review state, and artifacts
   - operate the dashboard and inspector

## Prerequisites

### Collection path

The active collection path still depends on:
- an authenticated Chrome tab already open on the target Facebook group
- the current browser-control bridge (`openclaw browser ...`)
- a `--source-key` for the source being collected

For `ingest:loop`, you also need:
- `--d

*[truncated — see source for full prompt]*