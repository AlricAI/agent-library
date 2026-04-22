# Knowledge Base

> This document describes the hybrid knowledge-base system used across all agent sessions in this framework.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Knowledge Base Pattern

This document describes the hybrid knowledge-base system used across all agent sessions in this framework.

## Overview

The knowledge base follows a **hybrid pattern**: a small always-loaded core plus semantic retrieval from Qdrant for the rest. This keeps initialization token costs low while retaining full context when needed.

```
knowledge/
├── core.md          ← always injected (≤500 tokens)
├── voice.md         ← writing style & tone
├── preferences.md   ← development conventions
├── prohibitions.md  ← things to never do
├── technical.md     ← architecture & env vars
└── project-facts.md ← team, timeline, decisions log
```

## Two Layers

### Layer 1 — Always Loaded (`core.md`)

`knowledge/core.md` is injected into every agent dispatch, regardless of Qdrant availability. Keep it under ~500 tokens. It should contain only:

- Project name and primary tech stack
- Non-negotiable rules (security, testing, style)

### Layer 2 — Semantically Retrieved (Qdrant, all other files)

All `knowledge/*.md` files except `core.md` are synced to Qdrant (type `knowledge`). At dispatch time the orchestrator retrieves only the chunks relevant to the current task, reducing token overhead by 80–95%.

**Fallback:** when Qdrant is unreachable, all `knowledge/*.md` files are loaded directly into the payload (Option A degraded mode — functional but burns more tokens).

## Setup

### 1. Fill in your knowledge files

Edit the files in `knowledge/` with project-specific information.

### 2. Sync to Qdrant

```bash
# Sync once (re-runnable — uses deterministic IDs so no duplicates)
python3 execution/memory_manager.py knowledge-sync --project <your-project>

# Optionally specify a custom knowledge directory
python3 execution/memory_manager.py knowledge-sync --project <your-project> --dir path/to/knowledge
```

### 3. Wire into agent dispatches

`dispatch_agent_team.py` auto-injects knowledge context whenever it builds a manifest. No extra configuration is needed af

*[truncated — see source for full prompt]*