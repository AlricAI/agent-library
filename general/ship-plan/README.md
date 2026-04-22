# SHIP PLAN

> Definitive plan for getting `nyc-housing-scout` from the current local operator pipeline to a shipped product.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Ship Plan

Definitive plan for getting `nyc-housing-scout` from the current local operator pipeline to a shipped product.

Use this doc to:

- align work across collection, processing, publication, and frontend
- sequence major milestones without dropping into implementation minutiae
- benchmark progress against the actual shipped end state

Use other docs for adjacent concerns:

- `docs/VISION_AND_ARCHITECTURE.md` for the durable architectural principles
- `docs/ROADMAP.md` for short-form status
- `docs/PIPELINE.md` for the current command surface and operational behavior
- `docs/LISTING_SCHEMA.md` for the normalized listing contract
- `docs/reviews/2026-03-16_00-40-29_CLOUDFLARE_DEPLOYMENT_READINESS_REVIEW.md` for the detailed Cloudflare assessment

## Product Definition

The product is shipped when it can do all of the following reliably:

1. keep multiple Facebook housing groups attached to healthy browser tabs on one always-on laptop
2. collect new posts continuously without source/tab collisions
3. persist canonical local observations, artifacts, queue state, payloads, and listings in SQLite
4. process observations into normalized listing data through the central downstream pipeline
5. publish a curated public read model from local canonical state to the cloud
6. serve a public-facing Cloudflare frontend from that published read model
7. preserve a private local operator workflow for inspection, review, and debugging

This is not a “deploy the current local UI” plan. It is a “ship the actual product” plan.

## Locked Decisions

These decisions are no longer provisional:

- The laptop remains the canonical write-side for collection, raw artifacts, queue state, and operator state.
- SQLite remains the system of record locally.
- The browser-control dependency on OpenClaw should be replaced, not entrenched.
- The replacement browser bridge should be a thin repo-owned MV3 extension plus a localhost relay.
- One signed-in Chrome session with one group tab per sou

*[truncated — see source for full prompt]*