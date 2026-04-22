# 020 Whale Onchain Intelligence Source

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 020 — Whale & On-Chain Intelligence Source

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode.** 3. **Always kill terminals.** 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.**

---

## Task

Build `src/sources/whales.ts` — a whale tracking and on-chain intelligence adapter combining multiple services to monitor large transactions, smart money wallets, and token flows.

### APIs

```
https://api.whale-alert.io/v1           # Whale Alert (Env: WHALE_ALERT_API_KEY)
https://api.arkham.intelligence          # Arkham Intelligence (Env: ARKHAM_API_KEY) [if available]
https://api.etherscan.io/api             # Etherscan (Env: ETHERSCAN_API_KEY)
https://api.blockchair.com               # Blockchair (Env: BLOCKCHAIR_API_KEY)
```

### Zod Schemas

```typescript
const WhaleTransaction = z.object({
  id: z.string(),
  blockchain: z.string(),
  symbol: z.string(),
  hash: z.string(),
  from: z.object({
    address: z.string(),
    owner: z.string().optional(),    // labeled entity name
    ownerType: z.enum(['exchange', 'whale', 'fund', 'defi', 'unknown']).optional(),
  }),
  to: z.object({
    address: z.string(),
    owner: z.string().optional(),
    ownerType: z.enum(['exchange', 'whale', 'fund', 'defi', 'unknown']).optional(),
  }),
  amount: z.number(),
  amountUsd: z.number(),
  timestamp: z.number(),
  transactionType: z.enum([
    'exchange_deposit',
    'exchange_withdrawal',
    'whale_transfer',
    'defi_interaction',
    'bridge_transfer',
    'mint',
    'burn',
    'unknown',
  ]),
})

const WalletProfile = z.object({
  address: z.string(),
  label: z.string().optional(),
  chain: z.string(),
  firstSeen: z.string(),
  lastActive: z.st

*[truncated — see source for full prompt]*