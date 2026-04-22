# 016 Bybit Source

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 016 — ByBit Source Adapter (CEX + Derivatives)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** Real implementations only.
2. **TypeScript strict mode** — no `any`, no `@ts-ignore`.
3. **Always kill terminals**, **commit and push as `nirholas`**.
4. **If close to hallucinating** — stop and tell the prompter.
5. **Run `npx tsc --noEmit` and `npx vitest run`** after changes.

---

## Task

Build `src/sources/bybit.ts` — adapter for ByBit, a major CEX with spot, derivatives, and copy-trading. v5 unified API.

### API Base URL

```
https://api.bybit.com/v5      # v5 unified API
# No auth for public market data
# Rate limit: 120 req/min for public endpoints
```

### Requirements

#### 1. Base Client

```typescript
function bybitFetch<T>(category: string, path: string, params?: Record<string, string>, ttl?: number): Promise<T>
// Response: { retCode: 0, retMsg: "OK", result: { list: [...] }, time: ... }
// Unwrap result, throw on retCode !== 0
```

#### 2. Zod Schemas

- `BybitTicker` — symbol, lastPrice, highPrice24h, lowPrice24h, turnover24h, volume24h, bid1Price, ask1Price, prevPrice24h, price24hPcnt, markPrice, indexPrice, openInterestValue, fundingRate, nextFundingTime
- `BybitKline` — startTime, openPrice, highPrice, lowPrice, closePrice, volume, turnover
- `BybitOrderBook` — s (symbol), b (bids), a (asks), ts, u (update_id)
- `BybitInstrumentInfo` — symbol, contractType, status, baseCoin, quoteCoin, settleCoin, lotSizeFilter, priceFilter, leverageFilter, fundingInterval
- `BybitOpenInterest` — symbol, openInterest, timestamp
- `BybitInsurance` — coin, balance, value
- `BybitRiskLimit` — id, symbol, limit, maintainMargin, initialMargin, maxLeverage
- `BybitLongShortRatio` — buyRatio, sellRatio, timestamp

#### 3. Exported Functions

**Spot & Market:**

| 

*[truncated — see source for full prompt]*