# 11 Backend Route Hardening

> ## Context

You are working on the main API server in `src/routes/` of the crypto-vision monorepo. It's a Hono-based REST API running on port 8080 wit

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 11 — Backend API: Fix & Harden All Route Handlers

## Context

You are working on the main API server in `src/routes/` of the crypto-vision monorepo. It's a Hono-based REST API running on port 8080 with 39 route modules and 200+ endpoints.

The API uses:
- Hono v4.7 (HTTP framework)
- Zod for validation (`src/lib/validation.ts`, `src/lib/route-schemas.ts`)
- Custom error handling (`src/lib/api-error.ts` — `AppError` class)
- Response envelope (`src/lib/response-envelope.ts`)
- Rate limiting (`src/lib/rate-limit.ts`)
- Caching (`src/lib/cache.ts` — two-tier LRU + Redis)
- Multi-source fetcher (`src/lib/fetcher.ts` — circuit breaker, retries)
- Auth (`src/lib/auth.ts` — API key validation)

## Task

### 1. Audit Every Route Module

Go through each of the 39 route files in `src/routes/` and ensure:

**Error Handling:**
- Every async handler has try/catch
- Errors thrown as `AppError` with proper HTTP status codes
- Upstream API failures return 502 with descriptive message
- Validation failures return 400 with field-level errors
- Rate limit errors return 429 with `Retry-After` header

**Input Validation:**
- All query parameters validated with Zod schemas
- All path parameters validated (`:id` must be non-empty string, numeric where expected)
- Pagination validated: `page >= 1`, `limit` between 1 and 100
- Sort fields validated against allowlist
- No SQL injection vectors (all params sanitized)

**Response Consistency:**
- All responses use `response-envelope.ts` format: `{ success: true, data: ..., meta: { ... } }`
- Error responses: `{ success: false, error: { code, message, details? } }`
- Pagination in meta: `{ page, limit, total, totalPages }`
- Cache headers: `Cache-Control`, `ETag` where appropriate

**Caching:**
- Appropriate TTLs per endpoint type:
  - Prices/market data: 30-60s
  - News: 300s
  - Static data (about, docs): 3600s
  - User-specific (portfolio): no cache
- Using the two-tier cache (LRU + Redis)

### 2. Fix Known Route Issues

**High Pri

*[truncated — see source for full prompt]*