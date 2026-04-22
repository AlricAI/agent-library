# Robot Team Proof Motion Analytics Requirements 2026 04 10

> Date: 2026-04-10

Scope: repo-ready analytics requirements for the robot-team proof motion in `Blueprint-WebApp`.

## Purpose

This document translate

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Robot-Team Proof-Motion Analytics Requirements

Date: 2026-04-10

Scope: repo-ready analytics requirements for the robot-team proof motion in `Blueprint-WebApp`.

## Purpose

This document translates the robot-team demand playbook into the current repo contract for analytics.

It separates:

- event coverage that already exists in code
- proof-motion signals that are still missing
- reporting views growth should be able to build from the current `growth_events` and `inboundRequests.ops.proof_path` surfaces

The goal is measurement clarity, not a new service or a new source of truth.

## Source Of Truth

The current authoritative sources are:

- `growth_events` for first-party analytics event capture
- `inboundRequests.ops.proof_path` for proof-path milestone timestamps and manual ops backfills
- `client/src/lib/analytics.ts` for client event definitions
- `client/src/components/site/ContactForm.tsx` for intake capture events
- `client/src/pages/ExactSiteHostedReview.tsx` for exact-site review view events
- `client/src/pages/AdminLeads.tsx` for proof-path milestone updates from ops and review-link actions
- `server/routes/admin-leads.ts` for reporting over growth events and queue state
- `docs/proof-motion-tags.md` for the canonical buyer-target, proof-pack, and hosted-review tag vocabulary

## Existing Coverage

These proof-motion signals already exist in the repo:

| Signal | Current event or state | Where it exists |
| --- | --- | --- |
| exact-site landing view | `exact_site_review_view` | `client/src/pages/ExactSiteHostedReview.tsx` |
| proof-path stage update | `proof_path_stage_updated` | `client/src/lib/analytics.ts` and `client/src/pages/AdminLeads.tsx` |
| contact request started | `contact_request_started` | `client/src/lib/analytics.ts` and `client/src/components/site/ContactForm.tsx` |
| contact request submitted | `contact_request_submitted` | `client/src/lib/analytics.ts` and `client/src/components/site/ContactForm.tsx` |
| contact request completed 

*[truncated — see source for full prompt]*