# 031 Analytics Routes

> ## Preamble

You are an expert TypeScript engineer building **cryptocurrency.cv** — the most comprehensive free crypto API. Stack: **Hono + TypeScript

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 031 — Analytics Routes (Advanced Market Analytics)

## Preamble

You are an expert TypeScript engineer building **cryptocurrency.cv** — the most comprehensive free crypto API. Stack: **Hono + TypeScript + Node 22**, deployed to Google Cloud Run with Redis caching.

### Absolute Rules

1. **Never mock, stub, or fake anything.** Every function must do real work with real APIs.
2. **TypeScript strict mode** — no `any`, no `@ts-ignore`, no type assertions without justification.
3. **Always use `isBackground: true`** for terminal commands, then **always kill the terminal** after getting output.
4. **Before any git commit**: `git config user.name "nirholas" && git config user.email "nirholas@users.noreply.github.com"`
5. **Always stay on the current branch** — run `git branch --show-current` first and never switch.
6. **Run `npx tsc --noEmit` and `npx vitest run`** before committing. Fix all errors.
7. **Improve any existing code you touch** — Boy Scout Rule.

---

## Context

The project lives at `/workspaces/crypto-vision`. Key paths:
- `src/routes/analytics.ts` — the route file to build/improve (currently 433 lines, 11 endpoints)
- `src/sources/coingecko.ts` — CoinGecko adapter (223 lines, 14 exports)
- `src/sources/defillama.ts` — DeFiLlama adapter (326 lines, 22 exports)
- `src/sources/alternative.ts` — Alternative.me + free APIs (1171 lines, 77 exports)
- `src/sources/cryptocompare.ts` — CryptoCompare adapter (211 lines, 14 exports)
- `src/sources/messari.ts` — Messari adapter (171 lines, 6 exports)
- `src/lib/api-error.ts` — Error factory (240 lines)
- `src/lib/validation.ts` — Zod validation helpers (275 lines)
- `src/lib/cache.ts` — Two-tier caching (235 lines)
- `src/lib/fetcher.ts` — HTTP client with retries + circuit breaker (214 lines)

---

## Task

Build comprehensive analytics routes in `src/routes/analytics.ts`. These are computed endpoints that aggregate data from multiple sources, perform calculations, and return derived insights that no single

*[truncated — see source for full prompt]*