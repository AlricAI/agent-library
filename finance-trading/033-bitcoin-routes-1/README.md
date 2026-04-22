# 033 Bitcoin Routes

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 033 — Bitcoin Routes (Bitcoin-Specific Analytics)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode** — no `any`. 3. **Always kill terminals** after every command. 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.** 7. **Improve any existing code you touch.**

---

## Task

Build / improve `src/routes/bitcoin.ts` — Bitcoin-specific blockchain analytics, mining data, Lightning Network stats, and on-chain metrics.

### Source Imports

```typescript
import { Hono } from 'hono';
import * as bitcoin from '../sources/bitcoin.js';
import * as blockchain from '../sources/blockchain.js';
import * as cg from '../sources/coingecko.js';
import { ApiError } from '../lib/api-error.js';

export const bitcoinRoutes = new Hono();
```

### Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/overview` | Bitcoin market + on-chain overview |
| GET | `/price` | BTC price from multiple sources |
| GET | `/metrics` | On-chain metrics (active addresses, hash rate, etc.) |
| GET | `/mining` | Mining statistics (difficulty, hash rate, revenue) |
| GET | `/mempool` | Mempool stats (tx count, size, fee estimates) |
| GET | `/fees` | Fee estimates by priority |
| GET | `/address/:address` | Bitcoin address balance and history |
| GET | `/tx/:txid` | Transaction detail |
| GET | `/block/:height` | Block detail |
| GET | `/blocks/latest` | Latest blocks |
| GET | `/halving` | Next halving countdown |
| GET | `/supply` | Supply breakdown (mined, lost, held) |
| GET | `/utxo-stats` | UTXO set statistics |
| GET | `/lightning` | Lightning Network statistics |
| GET | `/dominance` | BTC dominance chart |
| GET | `/stock-to-flow` | Stock-to-f

*[truncated — see source for full prompt]*