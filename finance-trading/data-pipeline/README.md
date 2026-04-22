# DATA PIPELINE

> > Ingestion workers, data flow, and storage architecture for Crypto Vision.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Data Pipeline

> Ingestion workers, data flow, and storage architecture for Crypto Vision.

## Overview

Crypto Vision ingests cryptocurrency data from 37+ upstream sources through a pipeline of scheduled workers. Data flows through two paths simultaneously:

1. **BigQuery** — immutable OLAP storage for historical analytics
2. **Pub/Sub** — real-time streaming for downstream consumers

```
┌────────────────────┐
│  Upstream APIs      │
│  (37+ sources)     │
└────────┬───────────┘
         │
┌────────▼───────────┐
│  Ingestion Workers  │
│  (8 workers)       │
└────┬──────────┬────┘
     │          │
┌────▼────┐ ┌──▼──────┐
│ BigQuery│ │ Pub/Sub  │
│ (OLAP)  │ │ (stream) │
└─────────┘ └──┬──────┘
               │
         ┌─────▼──────┐
         │ Consumers   │
         │ (API cache, │
         │  ML, alerts)│
         └─────────────┘
```

## Workers

All workers extend `WorkerBase` (`src/workers/worker-base.ts`), which provides:

- **Periodic fetching** — configurable interval per worker
- **Dual-write** — BigQuery streaming insert + Pub/Sub publish
- **Exponential backoff** — automatic retry with jitter on failures
- **Prometheus metrics** — ingestion count, latency, error rate
- **Graceful shutdown** — SIGTERM/SIGINT handling with drain

### Worker Registry

| Worker | File | Schedule | Source | Data |
|--------|------|----------|--------|------|
| Market | `ingest-market.ts` | Every 2 min | CoinGecko | Top coins, prices, market caps, volumes |
| DeFi | `ingest-defi.ts` | Every 5 min | DeFiLlama | Protocol TVL, yields, stablecoins, fees |
| News | `ingest-news.ts` | Every 5 min | RSS (130+ feeds) | Aggregated crypto news articles |
| DEX | `ingest-dex.ts` | Every 2 min | GeckoTerminal | DEX pair data, liquidity, volume |
| Derivatives | `ingest-derivatives.ts` | Every 5 min | CoinGlass | Funding rates, OI, liquidations |
| On-Chain | `ingest-onchain.ts` | Every 5 min | mempool.space, Etherscan | Gas, fees, network stats |
| Governance | `ingest-governance.ts` |

*[truncated — see source for full prompt]*