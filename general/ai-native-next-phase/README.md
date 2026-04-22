# Ai Native Next Phase

> This document captures the repo-side implementation of Blueprint's next phase:

- one narrow commercial wedge: **Exact-Site Hosted Review**
- stronger

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Blueprint Next-Phase Loops

This document captures the repo-side implementation of Blueprint's next phase:

- one narrow commercial wedge: **Exact-Site Hosted Review**
- stronger growth telemetry and attribution
- proof-led creative generation
- voice concierge support with hard guardrails
- operator loops that convert customer signal into internal execution work
- approval-gated campaign sends and lifecycle emails through the existing action ledger

## Current Wedge

**Exact-Site Hosted Review** means:

- one real facility
- one workflow lane
- one package-plus-hosted-review path
- explicit human gates on pricing, legal, rights, privacy, security, and other irreversible commitments

The public landing route is `/exact-site-hosted-review`.

## Growth Loop

Implemented surfaces:

- client analytics now mirror page views and events into a first-party `/api/analytics/ingest` stream when `BLUEPRINT_ANALYTICS_INGEST_ENABLED=1`
- experiment assignment is deterministic in `client/src/lib/experiments.ts`
- wedge-specific experiment exposure and conversion events are emitted through `client/src/lib/analytics.ts`
- top-level hosted-review CTAs now point at the narrow wedge route instead of the broad contact path

## Creative Loop

Implemented surfaces:

- protected campaign-kit builder at `/admin/growth-studio`
- `POST /api/admin/creative/campaign-kit` for proof-led landing/email/outbound/reel kits
- `POST /api/admin/creative/generate-image` is disabled by policy for server-side paid image generation
- `POST /api/admin/creative/generate-video` plus `GET /api/admin/creative/video-tasks/:taskId` for OpenRouter-backed video generation when `OPENROUTER_API_KEY` is configured
- `POST /api/admin/creative/render-proof-reel` for local Remotion proof-reel rendering

This creative loop now splits by medium:

- image-heavy execution routes to Codex lanes rather than server-side paid image APIs
- video remains on the server-side/provider-based path

The creative system is intentionally

*[truncated — see source for full prompt]*