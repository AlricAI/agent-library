# 032 Whale Social Routes

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 032 — Whale & Social Routes (Whale Watching + Social Signals)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode** — no `any`. 3. **Always kill terminals** after every command. 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.** 7. **Improve any existing code you touch.**

---

## Task

Build / improve `src/routes/whales.ts` and `src/routes/social.ts` — whale transaction monitoring and social media signal aggregation.

### Source Imports

```typescript
// whales.ts
import { Hono } from 'hono';
import * as whaleSource from '../sources/whales.js';
import { ApiError } from '../lib/api-error.js';
export const whaleRoutes = new Hono();

// social.ts
import { Hono } from 'hono';
import * as cryptocompare from '../sources/cryptocompare.js';
import { ApiError } from '../lib/api-error.js';
export const socialRoutes = new Hono();
```

### Whale Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/transactions` | Recent whale transactions (>$100K) |
| GET | `/transactions/:symbol` | Whale txs for specific token |
| GET | `/alerts` | Generated whale alerts |
| GET | `/smart-money` | Smart money movement tracker |
| GET | `/smart-money/:token` | Smart money trades for token |
| GET | `/exchange-flows` | Exchange deposit/withdrawal flows |
| GET | `/exchange-flows/:symbol` | Token exchange flows |
| GET | `/wallets/top/:chain` | Top wallets by holdings |
| GET | `/wallets/:address` | Wallet profile & activity |
| GET | `/wallets/:address/track` | Track a wallet (add to watchlist) |
| GET | `/accumulation/:symbol` | Accumulation/distribution signal |
| GET | `/dormant` | Recently active dormant wallets |

### Social Endpoi

*[truncated — see source for full prompt]*