# 017 Okx Source

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 017 — OKX Source Adapter (CEX + DEX Aggregator)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode.** 3. **Always kill terminals.** 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.**

---

## Task

Build `src/sources/okx.ts` — adapter for OKX, a top-3 CEX with comprehensive market data APIs. No auth for public endpoints.

### API Base URL

```
https://www.okx.com/api/v5     # v5 API
# Public endpoints: no auth needed
# Rate limit: 20 req/2s per endpoint
```

### Requirements

#### 1. Response Wrapper

```typescript
// OKX wraps all responses: { code: "0", msg: "", data: [...] }
// code "0" = success, anything else = error
function okxFetch<T>(path: string, params?: Record<string, string>, ttl?: number): Promise<T[]>
```

#### 2. Zod Schemas

- `OkxTicker` — instId, last, lastSz, askPx, askSz, bidPx, bidSz, open24h, high24h, low24h, volCcy24h, vol24h, sodUtc0, sodUtc8, ts
- `OkxCandle` — [ts, o, h, l, c, vol, volCcy, volCcyQuote, confirm]
- `OkxOrderBook` — asks[][], bids[][], ts
- `OkxInstrument` — instType, instId, uly, instFamily, baseCcy, quoteCcy, settleCcy, ctVal, ctMult, ctType, expTime, lever, tickSz, lotSz, minSz, state
- `OkxFundingRate` — instId, fundingRate, nextFundingRate, fundingTime, nextFundingTime
- `OkxOpenInterest` — instId, oi, oiCcy, ts
- `OkxLongShortRatio` — ts, oeRatio
- `OkxTakerVolume` — ts, sellVol, buyVol, ts

#### 3. Exported Functions

**Market Data:**

| Function | Endpoint | Cache TTL |
|----------|----------|-----------|
| `getTickers(instType)` | `/market/tickers` | 15s |
| `getTicker(instId)` | `/market/ticker` | 10s |
| `getCandles(instId, bar?, limit?)` | `/market/candles` | 30s |
| `getHistoryCandles(

*[truncated — see source for full prompt]*