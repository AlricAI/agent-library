# QUOTE CACHING

> Automated stock quote caching with 5-minute refresh intervals to ensure fast, up-to-date market data.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Stock Quote Caching System

Automated stock quote caching with 5-minute refresh intervals to ensure fast, up-to-date market data.

## Overview

The quote caching system keeps popular stock prices fresh by:
1. Caching quotes in the database for 5 minutes
2. Running a cron job every 5 minutes to refresh popular symbols
3. Serving cached data instantly to users (no API delays)

## Cache Configuration

### Cache TTL (Time-To-Live)

```typescript
const QUOTE_CACHE_TTL = 5 * 60 * 1000; // 5 minutes
```

Changed from 1 minute to 5 minutes to:
- Reduce API load on external providers
- Match cron job refresh interval
- Balance freshness with cost

### Database Storage

Quotes are cached in the `stock_quote_cache` table:

```sql
stock_quote_cache (
  symbol,           -- Stock ticker (e.g., "AAPL")
  price,            -- Current price
  change,           -- Price change
  changePercent,    -- % change
  open, high, low,  -- Daily stats
  previousClose,    -- Previous close
  volume,           -- Trading volume
  marketCap,        -- Market capitalization
  currency,         -- "USD", "EUR", etc.
  name,             -- Company name
  exchange,         -- Exchange name
  source,           -- Data provider
  lastFetched,      -- Cache timestamp
  createdAt,        -- First cached
  updatedAt         -- Last updated
)
```

## Cron Job: Quote Refresh

### Schedule
**Every 5 minutes** (`*/5 * * * *`)

### Endpoint
`/api/cron/refresh-quotes`

### Popular Symbols (35 stocks)

```typescript
// Tech Giants (7)
AAPL, MSFT, GOOGL, AMZN, META, NVDA, TSLA

// Major Index ETFs (4)
SPY, QQQ, DIA, IWM

// Financial (5)
JPM, BAC, WFC, GS, MS

// Tech & Payment (8)
NFLX, AMD, INTC, BABA, DIS, COIN, SQ, PYPL, V, MA

// Energy (2)
XOM, CVX

// Healthcare (3)
JNJ, PFE, UNH

// Consumer (4)
WMT, HD, MCD, NKE
```

### Why These Symbols?

Selected based on:
- **Trading volume**: Most actively traded stocks
- **User interest**: Commonly viewed/traded
- **Market representation**: Covers major sectors

*[truncated — see source for full prompt]*