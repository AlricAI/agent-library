# Gbrain Pattern Adaptation Plan 2026 04 10

> Date: 2026-04-10

Status: Proposed same-stack adaptation plan for `Blueprint-WebApp`

Scope: Bring the useful patterns from `gbrain` into Blueprint's 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GBrain Pattern Adaptation Plan

Date: 2026-04-10

Status: Proposed same-stack adaptation plan for `Blueprint-WebApp`

Scope: Bring the useful patterns from `gbrain` into Blueprint's existing repo, KB, agent runtime, and Paperclip routines without adding Supabase, Postgres, or a second operational datastore.

## Decision

Blueprint should adopt the **pattern** behind `gbrain`, not the shipped `gbrain` storage/runtime stack.

Blueprint should borrow:

- brain-first lookup before external research
- compiled-truth plus append-only signal history
- stronger entity/page discipline
- routine background hygiene and contradiction cleanup
- better attachment of durable research context into agent sessions

Blueprint should not adopt:

- Supabase as a new required service
- `gbrain` as a runtime dependency of `Blueprint-WebApp`
- a second canonical ops datastore
- a generic personal-memex schema that competes with Blueprint doctrine or product truth

This plan stays consistent with:

- `AUTONOMOUS_ORG.md`
- `docs/ai-tooling-adoption-implementation-2026-04-07.md`
- `docs/ai-skills-governance-2026-04-07.md`
- `docs/hermes-kb-design.md`

## Why This Fits Blueprint

`gbrain` is strongest where Blueprint still has room to improve:

- compounding research memory across agent runs
- reusable buyer and market context
- better continuity between daily research loops and operator sessions
- stronger "read existing context first" discipline before expensive or noisy external research

Blueprint already has the right primitives:

- Paperclip as execution and ownership truth
- Notion as workspace and operator surface
- Firebase / Firestore as operational system of record
- a constrained Hermes KB under `knowledge/`
- attachable startup context in the agent runtime

The gap is not storage. The gap is **discipline and retrieval ergonomics** across these existing layers.

## Blueprint-Specific Adaptation Target

Do not build a generic personal memex.

Build a **Blueprint research brain** o

*[truncated — see source for full prompt]*