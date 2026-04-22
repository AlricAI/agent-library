# 021 Market Routes

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 021 — Market Routes (Core Market Data API)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode** — no `any`. 3. **Always kill terminals** after every command. 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.** 7. **Improve any existing code you touch.**

---

## Task

Build / improve `src/routes/market.ts` — the primary market data route module. This is the highest-traffic set of endpoints and must be production-grade.

### Route Pattern

```typescript
import { Hono } from 'hono';
import * as cg from '../sources/coingecko.js';
import * as alt from '../sources/alternative.js';
import * as coinlore from '../sources/coinlore.js';
import { ApiError } from '../lib/api-error.js';

export const marketRoutes = new Hono();
```

### Endpoints to Implement

| Method | Path | Description | Source |
|--------|------|-------------|--------|
| GET | `/coins` | Top coins by market cap, paginated | CoinGecko |
| GET | `/coin/:id` | Detailed coin data (description, links, stats) | CoinGecko |
| GET | `/price` | Simple multi-coin price lookup (`?ids=bitcoin,ethereum`) | CoinGecko |
| GET | `/trending` | Trending coins (top 15) | CoinGecko |
| GET | `/global` | Global market stats (total mcap, volume, dominance) | CoinGecko |
| GET | `/search` | Search coins by name/symbol | CoinGecko |
| GET | `/chart/:id` | Price chart data with configurable timeframe | CoinGecko |
| GET | `/ohlc/:id` | OHLC candle data | CoinGecko |
| GET | `/exchanges` | Exchange rankings by volume | CoinGecko |
| GET | `/categories` | Market categories with aggregate stats | CoinGecko |
| GET | `/fear-greed` | Fear & Greed Index (current + historical) | Alternative.me |
| GET | `/gainers

*[truncated — see source for full prompt]*