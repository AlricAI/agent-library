# Graphify Pilot Corpus Policy 2026 04 07

> Date: 2026-04-07

Status: Active pilot policy

Scope: First-pass corpus and run policy for graphify-style derived graph generation in `Blueprint-WebAp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Graphify Pilot Corpus Policy

Date: 2026-04-07

Status: Active pilot policy

Scope: First-pass corpus and run policy for graphify-style derived graph generation in `Blueprint-WebApp`.

## Purpose

This file makes the initial graph pilot executable without ambiguity.

It defines:

- what the first pilot is allowed to ingest
- what must stay out by default
- where derived graph outputs belong
- how findings may be promoted back into reviewed Blueprint artifacts

This policy must be read together with:

- `docs/graphify-adoption-implementation-2026-04-07.md`
- `docs/hermes-kb-design.md`
- `docs/ai-skills-governance-2026-04-07.md`
- `PLATFORM_CONTEXT.md`
- `WORLD_MODEL_STRATEGY_CONTEXT.md`
- `AUTONOMOUS_ORG.md`

## Core Rule

The pilot is for structure discovery, not authority creation.

Graph outputs may help agents and humans understand the repo faster.
They may not override repo doctrine, Paperclip state, Firestore state, Notion review state, rights/provenance truth, or package/runtime truth.

## Pilot Goal

The first pilot should answer these questions:

1. Which modules and docs are the structural centers of the current autonomous-org and ops-automation implementation?
2. Where do doctrine files map into code, routines, and review surfaces?
3. What contradictions, overlaps, stale assumptions, or missing links are visible once docs and implementation are graphed together?
4. Can those findings be promoted into `knowledge/indexes/` or reviewed reports without creating a second authority layer?

## Allowed Inputs

The first pilot may include:

- `PLATFORM_CONTEXT.md`
- `WORLD_MODEL_STRATEGY_CONTEXT.md`
- `AUTONOMOUS_ORG.md`
- `docs/`
- `knowledge/compiled/`
- `knowledge/indexes/`
- `knowledge/README.md`
- `knowledge/AGENTS.md`
- `ops/paperclip/`
- `server/agents/`
- `server/utils/opsAutomationScheduler.ts`
- `server/utils/agent-graduation.ts`
- `server/utils/notion-sync.ts`
- `server/utils/autonomous-growth.ts`
- `server/routes/admin-agent.ts`
- `server/routes/admin

*[truncated — see source for full prompt]*