# 12 Backend Source Adapters

> ## Context

You are working on `src/sources/` in the crypto-vision monorepo. There are 37 data source adapters that connect to external APIs. Each ada

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 12 — Backend: Data Source Adapters Audit & Fix

## Context

You are working on `src/sources/` in the crypto-vision monorepo. There are 37 data source adapters that connect to external APIs. Each adapter fetches data from a specific service and normalizes it for the route handlers.

The adapters use:
- `src/lib/fetcher.ts` — HTTP client with circuit breaker, retries, timeout
- `src/lib/cache.ts` — Two-tier caching (LRU + Redis)
- `src/lib/coingecko-rate-limit.ts` — CoinGecko-specific rate limiter
- `src/lib/logger.ts` — Structured logging

## All 37 Source Adapters

| Adapter | External API | Priority |
|---------|-------------|----------|
| `coingecko.ts` | CoinGecko v3 | Critical |
| `defillama.ts` | DeFiLlama | Critical |
| `binance.ts` | Binance Public API | Critical |
| `bitcoin.ts` | BlockCypher, Mempool.space | High |
| `blockchain.ts` | Blockchain.info | High |
| `geckoterminal.ts` | GeckoTerminal DEX API | High |
| `alternative.ts` | Alternative.me (F&G Index) | High |
| `cryptocompare.ts` | CryptoCompare | Medium |
| `coinglass.ts` | CoinGlass derivatives | Medium |
| `hyperliquid.ts` | Hyperliquid DEX | Medium |
| `dydx.ts` | dYdX v4 | Medium |
| `deribit.ts` | Deribit options | Medium |
| `jupiter.ts` | Jupiter Solana DEX | Medium |
| `snapshot.ts` | Snapshot.org governance | Medium |
| `l2beat.ts` | L2Beat analytics | Medium |
| `coincap.ts` | CoinCap.io | Medium |
| `coinlore.ts` | CoinLore | Low |
| `bybit.ts` | Bybit API | Medium |
| `okx.ts` | OKX API | Medium |
| `macro.ts` | Yahoo Finance, FRED | Medium |
| `etf.ts` | ETF data sources | Medium |
| `staking.ts` | StakingRewards | Medium |
| `unlocks.ts` | Token.Unlocks | Medium |
| `whales.ts` | Whale Alert, Arkham | Medium |
| `social.ts` | LunarCrush, Santiment | Medium |
| `nft.ts` | OpenSea, Reservoir | Low |
| `oracles.ts` | Chainlink, Pyth | Medium |
| `depinscan.ts` | DePINscan | Low |
| `tokenterminal.ts` | Token Terminal | Low |
| `messari.ts` | Messari | Low |
| `goplus.ts` | GoPl

*[truncated — see source for full prompt]*