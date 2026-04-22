# Market Data

> How to use the market data components for real-time crypto prices, news, and analytics.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Market Data Guide

How to use the market data components for real-time crypto prices, news, and analytics.

> **New to market data?** See the [Glossary](GLOSSARY.md) for definitions of terms like TVL, Fear & Greed Index, and market cap.

---

## Overview

The toolkit includes two market data components:

| Component | What It Does | Sources |
|-----------|-------------|---------|
| **Crypto Market Data** | Prices, market caps, TVL, sentiment | CoinGecko, DeFiLlama, Alternative.me |
| **Crypto News** | Headlines from 200+ sources | RSS, APIs, scraping |

---

## Crypto Market Data

**Location:** `market-data/crypto-market-data/`

A zero-dependency TypeScript library for fetching cryptocurrency market data.

### Features

- **CoinGecko** — Prices, market caps, trading volume, historical data
- **DeFiLlama** — Total Value Locked (TVL), protocol data, yields
- **Fear & Greed Index** — Market sentiment (0-100 scale)
- Smart caching with configurable TTL
- Automatic rate limiting with retry
- Edge Runtime compatible (Cloudflare Workers, Vercel Edge)

### Quick Start

```typescript
import { CoinGecko, DeFiLlama, FearAndGreed } from '@nirholas/crypto-market-data';

// Get Bitcoin price
const btc = await CoinGecko.getPrice('bitcoin');
console.log(`BTC: $${btc.usd}`);

// Get BNB Chain TVL
const bnbTvl = await DeFiLlama.getProtocolTvl('binance');
console.log(`BNB Chain TVL: $${bnbTvl}`);

// Get market sentiment
const sentiment = await FearAndGreed.getIndex();
console.log(`Market sentiment: ${sentiment.value} (${sentiment.classification})`);
```

### Configuration

```typescript
const client = new CoinGecko({
  cacheTtl: 60_000,        // Cache for 60 seconds
  maxRetries: 3,            // Retry up to 3 times
  rateLimit: 10,            // 10 requests per second
});
```

### Available Methods

| Provider | Method | Description |
|----------|--------|-------------|
| CoinGecko | `getPrice(id)` | Current price in USD |
| CoinGecko | `getMarketData(id)` | Full market data (cap

*[truncated — see source for full prompt]*