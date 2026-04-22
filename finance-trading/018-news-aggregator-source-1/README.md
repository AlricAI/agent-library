# 018 News Aggregator Source

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 018 — News Aggregator Source (Multi-Provider News)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode.** 3. **Always kill terminals.** 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.**

---

## Task

Build `src/sources/news-aggregator.ts` — a unified news aggregation adapter pulling from multiple crypto news APIs, normalizing them into a single feed. Also build `src/sources/crypto-news.ts` for the CryptoPanic API.

### APIs

```
https://cryptopanic.com/api/v1        # CryptoPanic (Env: CRYPTOPANIC_API_KEY)
https://min-api.cryptocompare.com      # CryptoCompare news (already have key)
https://newsdata.io/api/1              # NewsData.io (Env: NEWSDATA_API_KEY) [optional]
```

### Requirements

#### 1. Unified News Schema

```typescript
const NormalizedArticle = z.object({
  id: z.string(),
  title: z.string(),
  summary: z.string().optional(),
  body: z.string().optional(),
  url: z.string().url(),
  source: z.string(),             // "cryptopanic", "cryptocompare", "newsdata"
  sourceUrl: z.string().optional(),
  author: z.string().optional(),
  publishedAt: z.string().datetime(),
  categories: z.array(z.string()),
  coins: z.array(z.object({       // mentioned coins
    symbol: z.string(),
    name: z.string().optional(),
  })),
  sentiment: z.enum(['positive', 'negative', 'neutral']).optional(),
  importance: z.enum(['high', 'medium', 'low']).optional(),
  imageUrl: z.string().optional(),
  votes: z.object({
    positive: z.number(),
    negative: z.number(),
    important: z.number(),
    liked: z.number(),
    disliked: z.number(),
    lol: z.number(),
    toxic: z.number(),
    saved: z.number(),
    comments: z.number(),
  }).optio

*[truncated — see source for full prompt]*