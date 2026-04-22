# DATA SOURCES

> > Complete reference for all external data sources integrated into Crypto Vision.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Data Sources

> Complete reference for all external data sources integrated into Crypto Vision.

## Table of Contents

1. [Overview](#overview)
2. [Market Data](#market-data)
3. [DeFi](#defi)
4. [News & Social](#news--social)
5. [On-Chain](#on-chain)
6. [Derivatives & Perps](#derivatives--perps)
7. [Security & Auditing](#security--auditing)
8. [Governance & Research](#governance--research)
9. [Macro & TradFi](#macro--tradfi)
10. [Source Adapter Architecture](#source-adapter-architecture)
11. [Rate Limits & Caching](#rate-limits--caching)

---

## Overview

Crypto Vision integrates **37+ external data sources** through source adapters located in `src/sources/`. Each adapter handles authentication, rate limiting, error handling, and response normalization.

| Category | Sources | Adapter Count |
|----------|---------|---------------|
| Market Data | CoinGecko, CoinCap, CoinLore, CoinPaprika, CryptoCompare | 5 |
| DeFi | DeFiLlama, TokenTerminal | 2 |
| DEX | GeckoTerminal, Jupiter | 2 |
| CEX | Binance, Bybit, OKX | 3 |
| Derivatives | Deribit, dYdX, Hyperliquid | 3 |
| News | RSS Aggregator (130+ feeds), Crypto News API | 2 |
| Social | LunarCrush, CryptoCompare Social | 2 |
| On-Chain | mempool.space, Blockchain.info, Etherscan, Blockchair | 4 |
| Security | GoPlus | 1 |
| Governance | Snapshot | 1 |
| NFT | Reservoir | 1 |
| Oracles | Chainlink, DIA, Pyth | 3 |
| Staking | Rated.network | 1 |
| L2 | L2Beat | 1 |
| DePIN | DePINScan | 1 |
| Calendar | CoinMarketCal | 1 |
| Research | Messari | 1 |
| Macro | Yahoo Finance | 1 |
| Sentiment | Alternative.me | 1 |
| Unlocks | Token unlock trackers | 1 |

---

## Market Data

### CoinGecko

| Field | Value |
|-------|-------|
| Adapter | `src/sources/coingecko.ts` |
| Base URL | `https://api.coingecko.com/api/v3` (free) or `https://pro-api.coingecko.com/api/v3` (pro) |
| Auth | Optional `x-cg-demo-key` or `x-cg-pro-api-key` header |
| Rate Limit | 30 req/min (free), 500 req/min (pro) |
| Cache TTL | 60s (prices), 300s

*[truncated — see source for full prompt]*