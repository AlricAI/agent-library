# PRD Partner Directory Expansion

> **Owner:** Atlas / Sage | **Date:** 2026-04-14 | **Status:** Draft

## 1. Problem Statement

Coherence Daddy leadership is now physically vetting loca

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PRD: Partner + Directory Expansion

**Owner:** Atlas / Sage | **Date:** 2026-04-14 | **Status:** Draft

## 1. Problem Statement

Coherence Daddy leadership is now physically vetting local partners (gyms, niche service businesses) on the road, but the current `partner_companies` schema has no concept of *in-person vetting*, no geolocation, and no structured services/hours beyond loose jsonb blobs. Scaling from 1 to 100 vetted partners will outpace the current admin workflow and the 6-personality content engine, which generates broad blog posts rather than hyper-local long-tail articles. Simultaneously, the 532-slug Project Directory refreshes on a 1–4hr intel cron that hits *everything* uniformly — priority entries get no special treatment, and stale data is visible to users because no `last_updated` field is exposed. The long-tail niche query space ("24/7 gyms Colorado Springs", "raw diet for dogs Austin") is entirely uncaptured.

## 2. Proposed Architecture

### D1. Vetted Partner Pipeline

**Purpose:** First-class support for in-person vetting with location, photos, and operational metadata.

- **Files to touch:**
  - `packages/db/src/schema/partners.ts` (extend `partnerCompanies`)
  - `server/src/routes/partner.ts` (new `POST /:slug/vet`, extend `PUT /:slug`)
  - `ui/src/pages/Partners.tsx` (admin vetting modal)
- **Schema additions** (new migration, e.g. `0066_partner_vetting.sql`):
  - `vetted_at timestamptz`, `vetted_by_agent text`, `vetting_notes text`
  - `visit_photos jsonb` (array of `{url, caption, takenAt}`)
  - `business_hours jsonb` (already have `hours` — reuse, standardize to 7-day object)
  - Promote `services` from jsonb to `services text[]` for GIN indexing
  - `lat numeric(10,7)`, `lng numeric(10,7)`, `geohash text`
  - Index: `(companyId, vetted_at)`, GIN on `services`
- **API:** `POST /api/partners/:slug/vet` (body: notes, photos[], hours, lat/lng) — marks `vetted_at=now()`, sets `vetted_by_agent` from auth context.
- **UI:** "Mark Vetted" bu

*[truncated — see source for full prompt]*