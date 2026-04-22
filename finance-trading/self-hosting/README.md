# SELF HOSTING

> ## Overview

This guide covers how to run the full Crypto Vision stack on any infrastructure
after GCP credits are exhausted. All artifacts — data, mo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Self-Hosting Crypto Vision After GCP Credits Expire

## Overview

This guide covers how to run the full Crypto Vision stack on any infrastructure
after GCP credits are exhausted. All artifacts — data, models, embeddings,
configurations — have been exported and are fully portable.

**Key principle**: every GCP service has an open-source or commodity equivalent.
The migration cost is operational, not technical.

---

## Table of Contents

1. [Exported Artifacts](#exported-artifacts)
2. [GCP Replacement Map](#gcp-replacement-map)
3. [BigQuery → PostgreSQL / DuckDB / ClickHouse](#bigquery-data-migration)
4. [Model Weights → Local GPU / Cloud GPU](#model-deployment)
5. [Embeddings → Self-Hosted Vector Database](#embeddings-migration)
6. [Infrastructure Replacement](#infrastructure-replacement)
7. [Minimal Self-Hosted Stack](#minimal-self-hosted-stack)
8. [Monthly Cost Estimates](#monthly-cost-estimates)
9. [Migration Timeline](#migration-timeline)
10. [Runbooks](#runbooks)

---

## Exported Artifacts

All artifacts are exported to `gs://{project}-exports/{export-id}/` with this
structure:

```
{export-id}/
├── manifest.json                    # Complete export manifest
├── bigquery/
│   ├── market_snapshots/            # Parquet + Snappy compressed
│   ├── ohlc_candles/
│   ├── defi_protocols/
│   ├── yield_pools/
│   ├── news_articles/
│   ├── fear_greed/
│   ├── dex_pairs/
│   ├── chain_tvl/
│   ├── exchange_snapshots/
│   ├── bitcoin_network/
│   ├── gas_prices/
│   ├── stablecoin_supply/
│   ├── funding_rounds/
│   ├── derivatives_snapshots/
│   ├── governance_proposals/
│   ├── whale_movements/
│   ├── agent_interactions/
│   ├── embeddings/                  # Parquet + JSONL (dual format)
│   ├── anomaly_events/
│   ├── search_analytics/
│   ├── training_pairs/
│   └── eval_results/
├── models/
│   ├── lora-adapters/               # LoRA weights (safetensors)
│   ├── quantized/                   # GPTQ 4-bit models
│   ├── training-data/               # JSONL tra

*[truncated — see source for full prompt]*