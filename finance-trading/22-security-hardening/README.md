# 22 Security Hardening

> ## Context

You are hardening the security of crypto-vision, a TypeScript crypto data platform handling sensitive financial data. The stack:

- **API 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 22 — Security Hardening & Input Validation

## Context

You are hardening the security of crypto-vision, a TypeScript crypto data platform handling sensitive financial data. The stack:

- **API server**: Hono v4.7 on Node.js 22, 200+ endpoints, serves market data, portfolios, AI predictions
- **Auth**: API key-based authentication for premium tiers + admin auth
- **External APIs**: 37 data source adapters sending HTTP requests to third-party APIs
- **Database**: PostgreSQL 16 (Drizzle ORM), Redis 7
- **Existing security surface**: `src/sources/goplus.ts` (token security scanning via GoPlus API)
- **Dashboard**: Next.js 15 with admin routes
- **Pump Agent Swarm**: Handles Solana private keys, wallet rotation, financial transactions
- **Payments**: x402 payment protocol support

Key files:
- `src/routes/` — 39 route modules
- `src/lib/` — shared libraries (cache, rate-limit, ai, bigquery, etc.)
- `src/sources/goplus.ts` — GoPlus token security checker
- `apps/dashboard/src/lib/` — Frontend auth, API clients
- `packages/pump-agent-swarm/src/` — Private key handling, wallet management
- `SECURITY.md` — Security policy

## Task

### 1. Input Validation (`src/lib/validation.ts`)

Create a Zod-based validation layer for all API inputs:

```typescript
import { z } from 'zod';

// Shared validators
export const CoinIdSchema = z.string()
  .min(1).max(100)
  .regex(/^[a-z0-9-]+$/, 'Invalid coin ID format');

export const SymbolSchema = z.string()
  .min(1).max(10)
  .regex(/^[A-Z0-9]+$/, 'Invalid symbol format')
  .transform(s => s.toUpperCase());

export const AddressSchema = z.string()
  .regex(/^(0x[a-fA-F0-9]{40}|[1-9A-HJ-NP-Za-km-z]{32,44})$/, 'Invalid address');

export const PaginationSchema = z.object({
  page: z.coerce.number().int().min(1).max(1000).default(1),
  limit: z.coerce.number().int().min(1).max(250).default(50),
});

export const DateRangeSchema = z.object({
  from: z.coerce.date().optional(),
  to: z.coerce.date().optional(),
}).refine(d => !d.fr

*[truncated — see source for full prompt]*