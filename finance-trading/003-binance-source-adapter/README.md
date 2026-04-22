# 003 Binance Source Adapter

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**, the most comprehensive crypto/DeFi API infrastruc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 003 — Binance Source Adapter (CEX Market Data)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**, the most comprehensive crypto/DeFi API infrastructure. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** Real implementations only.
2. **TypeScript strict mode** — no `any`, no `@ts-ignore`.
3. **Every async call** needs try/catch, every response needs validation.
4. **Always kill terminals** after commands complete.
5. **Always commit and push** as `nirholas`.
6. **If close to hallucinating** — stop and tell the prompter.
7. **Always improve existing code** you touch.
8. **Run `npx tsc --noEmit` and `npx vitest run`** after changes.

### Conventions

- `@/` alias → `src/`, `.js` extensions, named exports, Zod schemas
- `fetchJSON` from `@/lib/fetcher.js`, `cache.wrap()` for all fetches
- `log` from `@/lib/logger.js` for structured logging

---

## Task

Build the **complete Binance source adapter** at `src/sources/binance.ts`. Binance is the world's largest crypto exchange and provides extensive public APIs with no auth required for market data.

### API Base URLs

```
https://api.binance.com/api/v3         # Spot market
https://fapi.binance.com/fapi/v1       # USD-M Futures
https://dapi.binance.com/dapi/v1       # COIN-M Futures
https://api.binance.com/sapi/v1        # Additional endpoints
```

### Requirements

#### 1. Base Client

```typescript
function binanceFetch<T>(base: string, path: string, params?: Record<string, string>, ttl?: number): Promise<T>
```

- No auth for public market data endpoints
- Rate limit: 1200 weight/min (track via `X-MBX-USED-WEIGHT-1M` header)
- Handle IP bans gracefully (418/429 status codes)

#### 2. Zod Schemas

- `Ticker24h` — symbol, priceChange, priceChangePercent, weightedAvgPrice, prevClosePrice, lastPrice, volume, quoteVolume, openTime, closeTime, highPrice, lowPrice, 

*[truncated — see source for full prompt]*