# 005 Cryptocompare Source

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**, the most comprehensive crypto/DeFi API infrastruc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 005 — CryptoCompare Source Adapter

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

---

## Task

Build the **complete CryptoCompare source adapter** at `src/sources/cryptocompare.ts`. CryptoCompare provides historical OHLCV, social stats, mining data, exchange volumes, and news — complementing CoinGecko with unique datasets.

### API Base URL

```
https://min-api.cryptocompare.com/data    # All endpoints
# Auth: Apikey header or &api_key= query param
# Env: CRYPTOCOMPARE_API_KEY
```

### Requirements

#### 1. Base Client

```typescript
function ccFetch<T>(path: string, params?: Record<string, string>, ttl?: number): Promise<T>
```

- Auth via `Authorization: Apikey {key}` header
- Free tier: 100K calls/month, 50 calls/sec
- Handle `Response` field (CryptoCompare wraps errors in `{ Response: "Error", Message: "..." }`)

#### 2. Zod Schemas

- `HistoData` — time, open, high, low, close, volumefrom, volumeto, conversionType, conversionSymbol
- `PriceResponse` — `Record<string, Record<string, number>>` (multi from/to)
- `PairData` — exchange, fromSymbol, toSymbol, volume24h, volume24hTo, price, lastUpdate
- `TopExchangeVolu

*[truncated — see source for full prompt]*