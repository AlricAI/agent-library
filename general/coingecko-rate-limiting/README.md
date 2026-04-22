# COINGECKO RATE LIMITING

> ## Problem

The application was experiencing rate limit errors (HTTP 429) from the CoinGecko API. The free tier allows only 30 calls/min, but the app 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CoinGecko Rate Limiting Implementation

## Problem

The application was experiencing rate limit errors (HTTP 429) from the CoinGecko API. The free tier allows only 30 calls/min, but the app was making concurrent requests without respecting these limits, leading to `Rate limited by CoinGecko API` errors.

## Solution

Implemented a comprehensive **client-side rate limiting system** with three main components:

### 1. Token Bucket Algorithm (`src/lib/coingecko-rate-limit.ts`)

**Key Features:**
- **Token Bucket**: Smooth token distribution (1 token = 1 request)
- **Free tier**: 30 tokens/minute (0.5 tokens/second)
- **Pro tier**: 500 tokens/minute (with `COINGECKO_API_KEY` env var)
- **Request Queuing**: Automatic queueing when tokens unavailable
- **Adaptive Rate Learning**: Monitors `Retry-After` and rate limit headers from CoinGecko
- **Metrics Tracking**: Exposes stats via health endpoint

**Exports:**
- `waitForCoinGeckoToken()` - Acquires token with automatic queuing
- `updateRateLimitInfo(headers)` - Updates rate limit knowledge from responses
- `recordCoinGeckoSuccess/Failure()` - Tracks request outcomes
- `getCoinGeckoRateLimitStats()` - Returns current metrics
- `resetCoinGeckoRateLimit()` - Resets state (testing)

### 2. Integration with CoinGecko Source (`src/sources/coingecko.ts`)

**Changes:**
- Added `await waitForCoinGeckoToken()` before each API request
- Requests now go through rate limiter transparently
- Updated import to include rate limiter module
- No breaking changes to public API

**Cache TTL Improvements:**
- Market data: 60s → 180s (3 min)
- Coin details: 120s → 600s (10 min)
- Simple prices: 30s → 60s (1 min)
- Trending: 300s → 600s (10 min)
- Global stats: 120s → 600s (10 min)
- Market chart: 300s → 1800s (30 min) - *immutable historical data*
- **OHLC candles: 300s → 3600s (1 hour)** - *immutable historical data*
- Exchanges: 300s → 1800s (30 min)

### 3. Fetcher Integration (`src/lib/fetcher.ts`)

**Changes:**
- Added 429 status handli

*[truncated — see source for full prompt]*