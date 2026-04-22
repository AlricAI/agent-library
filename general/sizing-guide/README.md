# Sizing Guide

> Guidelines to estimate CPU, memory, and partitioning for Epona at scale.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sizing Guide

Guidelines to estimate CPU, memory, and partitioning for Epona at scale.

## Target Scale

- 1000 concurrent tenant engines across a cluster
- 100k–2M facts per tenant
- ~50–500 rules per tenant

## Memory Budget (Per Tenant)

- Working Memory (WMEs): ~150–300 bytes/term (Elixir struct/map + ETS overhead)
  - 2M facts ≈ 300–600 MB (varies with field counts, binaries)
- Alpha Memories (indexes): 0.5–1.0x of WMEs depending on number/selectivity of keys
- Beta Memories (tokens): 0.2–0.6x of WMEs depending on join fanout and refraction efficacy
- Refraction Table: 50–150 MB (bounded ETS with TTL/LRU)
- Total Estimate: 1.5–2.5 GB per tenant at 2M facts and 500 rules
Tune for your schemas and rules; run the included perf harness (to be added) with representative data.

## CPU and Partitions

- Cores: Reserve ~2–4 schedulers (cores) per large active tenant during heavy ingestion; less once steady-state
- Partitions: 16–64 per tenant; choose power-of-two aligned with schedulers
  - Partition key: Dominant join key (e.g., `employee_id`) to keep joins local
  - Use higher partition counts if latency spikes under contention

## Multi-Tenant Placement

- Per-node concurrency depends on tenant size mix; expect dozens of small tenants per node and few large tenants per node.
- Use a placement strategy to spread large tenants across nodes; co-locate small tenants opportunistically.
- Consider start-on-demand engines with snapshot restore for infrequent tenants to conserve memory.

## Engine Lifecycle at 1000 Tenants

- Idle eviction: Persist snapshot and stop idle tenant engines after a grace period; gRPC calls trigger start-on-demand.
- Cold start target: < 1s to serve basic operations using preloaded compiled networks and fast snapshot restore.
- Quotas: Per-tenant memory and compute budgets; shed load with backpressure when exceeded.

## Bulk Load vs Incremental

- Bulk load mode defers agenda firing and uses large batch sizes for initial ingestion
- Enable writ

*[truncated — see source for full prompt]*