# 17 Testing Integration E2e Load

> ## Context

You are working on integration and E2E tests for crypto-vision. The test infrastructure includes:

- `vitest.config.ts` — Unit/integration

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 17 — Testing: Integration, E2E & Load Tests

## Context

You are working on integration and E2E tests for crypto-vision. The test infrastructure includes:

- `vitest.config.ts` — Unit/integration test config
- `vitest.e2e.config.ts` — E2E config (starts real server via `tests/e2e/global-setup.ts`)
- `tests/e2e/smoke.test.ts` — Basic E2E smoke test
- `tests/integration/api-flows.test.ts` — Integration test
- `tests/fuzz/api-fuzz.test.ts` — Fuzz test
- `tests/benchmarks/` — Benchmark directory (empty)
- `tests/load/` — Load test directory (empty)

## Task

### 1. Fix E2E Test Suite

Review and fix `tests/e2e/global-setup.ts` to properly start/stop the API server:

```typescript
// Global setup should:
// 1. Start the Hono server on a random available port
// 2. Wait for /health to return 200
// 3. Export the base URL for test files
// 4. On teardown: gracefully stop the server
```

Fix `tests/e2e/smoke.test.ts` to test against the running server:

```typescript
// Smoke tests should verify:
// - GET /health returns 200 with status "healthy"
// - GET /api/market/prices returns valid market data
// - GET /api/market/trending returns trending coins
// - GET /api/defi/tvl returns DeFi TVL data
// - GET /api/gas returns gas prices
// - GET /api/ai/models returns available AI models
// - 404 for unknown routes
// - CORS headers present
```

### 2. Write Integration Tests (`tests/integration/`)

**`api-flows.test.ts`** — Complete user journey tests:

```typescript
// Flow 1: Market Research
// 1. GET /api/market/prices → get bitcoin ID
// 2. GET /api/market/coin/bitcoin → get detail
// 3. GET /api/analytics/correlation?coins=bitcoin,ethereum → get correlation
// 4. POST /api/ai/analyze → analyze bitcoin

// Flow 2: DeFi Research
// 1. GET /api/defi/protocols → list protocols
// 2. GET /api/defi/protocol/aave → get Aave detail
// 3. GET /api/defi/yields → get yield opportunities
// 4. GET /api/analytics/defi-comparison → compare protocols

// Flow 3: Portfolio Manage

*[truncated — see source for full prompt]*