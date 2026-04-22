# 16 Testing Route Coverage

> ## Context

You are working on route tests for the crypto-vision API. There are 39 route modules in `src/routes/` but only ~24 have tests in `src/rout

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 16 — Testing: Route Test Coverage

## Context

You are working on route tests for the crypto-vision API. There are 39 route modules in `src/routes/` but only ~24 have tests in `src/routes/__tests__/` and ~10 in `tests/routes/`.

**Test framework:** Vitest
**Config:** `vitest.config.ts` at project root
**Pattern:** Tests use Hono's `app.request()` for HTTP testing (no real server)
**Mocking:** Mock external API calls, test route logic

## Routes WITH Tests (verify they pass)

In `src/routes/__tests__/`: agents, aggregate, ai, analytics, bitcoin, cex, defi, depin, derivatives, dex, exchanges, gas, governance, keys, l2, macro, market, news, onchain, perps, research, search, security, solana

In `tests/routes/`: agents-orchestrate, anomaly, defi, health, market, portfolio, solana, staking, unlocks, whales

## Routes WITHOUT Tests (need new tests)

| Route | Endpoints | Priority |
|-------|-----------|----------|
| `calendar.ts` | GET /api/calendar/events | Medium |
| `crypto-vision.ts` | Bot endpoints | Low |
| `ecosystem.ts` | GET /api/ecosystem/* | Medium |
| `etf.ts` | GET /api/etf/* | Medium |
| `export.ts` | POST /api/export/* | High |
| `news-aggregator.ts` | GET /api/news-aggregator/* | Medium |
| `nft.ts` | GET /api/nft/* | Medium |
| `oracles.ts` | GET /api/oracles/* | Medium |
| `social.ts` | GET /api/social/* | Medium |
| `ws.ts` | WebSocket | High |

## Task

### 1. Fix Existing Tests

Run all existing tests and fix any failures:
```bash
cd /workspaces/crypto-vision && npm test
```

For each failing test:
- If the route changed, update the test to match
- If a mock is outdated, update the mock data
- If a type changed, update test types
- Do NOT skip or disable tests

### 2. Write New Route Tests

For each untested route, write comprehensive tests following the existing pattern.

**Test Pattern (example from existing tests):**
```typescript
import { describe, it, expect, vi, beforeEach } from 'vitest';
import { Hono } from 'hono';
import { routeModu

*[truncated — see source for full prompt]*