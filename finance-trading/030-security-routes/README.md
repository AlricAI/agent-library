# 030 Security Routes

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 030 — Security Routes (Token Audit & Contract Security)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode** — no `any`. 3. **Always kill terminals** after every command. 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.** 7. **Improve any existing code you touch.**

---

## Task

Build / improve `src/routes/security.ts` — token and contract security analysis using GoPlus, on-chain data, and DeFi hack databases.

### Source Imports

```typescript
import { Hono } from 'hono';
import * as goplus from '../sources/goplus.js';
import * as llama from '../sources/defillama.js';
import { ApiError } from '../lib/api-error.js';

export const securityRoutes = new Hono();
```

### Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/token/:chainId/:address` | Full token security audit |
| GET | `/approval/:chainId/:address` | Token approval security check |
| GET | `/nft/:chainId/:address` | NFT contract security |
| GET | `/address/:address` | Address reputation check |
| GET | `/dapp/:url` | dApp/phishing site check |
| GET | `/hacks` | Major DeFi hacks/exploits |
| GET | `/hacks/:protocol` | Specific protocol hack details |
| GET | `/rugpull-check/:chainId/:address` | Rug pull risk assessment |
| GET | `/honeypot/:chainId/:address` | Honeypot detection |
| GET | `/risk-score/:chainId/:address` | Aggregate risk score (0-100) |
| GET | `/audit-report/:protocol` | Known audit reports for protocol |
| GET | `/recent-exploits` | Recent exploit timeline |

### Token Security Audit

```typescript
securityRoutes.get('/token/:chainId/:address', async (c) => {
  const { chainId, address } = c.req.param();
  
  const security =

*[truncated — see source for full prompt]*