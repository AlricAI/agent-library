# 15 Backend Workers Pipeline

> ## Context

You are working on the data ingestion pipeline in `src/workers/` of the crypto-vision monorepo. There are 15 worker files that periodicall

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 15 — Backend: Workers & Data Pipeline

## Context

You are working on the data ingestion pipeline in `src/workers/` of the crypto-vision monorepo. There are 15 worker files that periodically fetch data from external APIs, write to BigQuery + Pub/Sub, and index into vector stores.

The workers use a shared base class:
- `src/workers/worker-base.ts` — Periodic fetch, BigQuery+Pub/Sub dual-write, metrics, backoff, graceful shutdown

## Workers

**Data Ingestion (fetch from APIs → store):**
| Worker | Schedule | Source | Data |
|--------|----------|--------|------|
| `ingest-market.ts` | 2 min | CoinGecko | Market snapshots, F&G index |
| `ingest-defi.ts` | 5 min | DeFiLlama | TVL, yields, stables, DEX vols, fees |
| `ingest-news.ts` | 5 min | CryptoPanic, RSS | News articles |
| `ingest-dex.ts` | 2 min | DexScreener, GeckoTerminal | DEX pairs, trades |
| `ingest-derivatives.ts` | 10 min | CoinGlass, Hyperliquid, dYdX, Deribit | Funding, OI, liquidations |
| `ingest-governance.ts` | 30 min | Snapshot | Governance proposals |
| `ingest-macro.ts` | 60 min | Yahoo Finance | Macro indicators (DXY, Gold, S&P) |
| `ingest-onchain.ts` | 5 min | Mempool.space, RPCs | Gas prices, BTC network stats |
| `backfill-historical.ts` | On-demand | Multiple | OHLC candles, historical TVL |

**Embedding/Indexing (process → vector store):**
| Worker | Schedule | Input | Output |
|--------|----------|-------|--------|
| `index-news.ts` | 5 min | News articles | Vector store (search) |
| `index-protocols.ts` | 15 min | Protocol metadata | Vector store (search) |
| `index-governance.ts` | 30 min | Governance proposals | Vector store (search) |
| `index-agents.ts` | Startup | Agent JSON definitions | Vector store (search) |
| `index.ts` | — | Orchestrator for all workers | — |

## Task

### 1. Fix the Worker Base Class

Review `src/workers/worker-base.ts` and ensure:

```typescript
// WorkerBase should:
// 1. Accept config: { name, intervalMs, batchSize }
// 2. Run on schedule: every 

*[truncated — see source for full prompt]*