---
name: Sizing Guide
description: Guidelines to estimate CPU, memory, and partitioning for Epona at scale.
model: claude-sonnet-4-5
---
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
- Enable write_concurrency on ETS tables; pause tracing; widen fire limits after initial build

## GC and BEAM Settings (Hints)

- `+sbwt none` (reduce busy wait) for high concurrency
- `+swt very_low` (shorter scheduler wakeup) on latency-sensitive nodes
- Pin long binaries (e.g., provenance) outside hot paths; prefer IDs

## Monitoring Thresholds

- p95 propagation latency per tenant < 1s for small deltas
- ETS memory per partition capped; backpressure when limit approached
- Agenda queue length per partition below configured `fire_limit * 2`

## Capacity Planning Examples

Example A — Mixed tenants on a 16-core, 64 GB node

- Assumptions: 1 large tenant (2M facts, ~2 GB), 8 medium tenants (500k facts, ~0.6–0.8 GB each), 30 small tenants (100k facts, ~0.15–0.25 GB each).
- Memory: ~2 GB + (8 × 0.7 GB) + (30 × 0.2 GB) ≈ 2 + 5.6 + 6 ≈ 13.6 GB engine state; add 30–50% headroom for code, caches, BEAM, OS.
- CPU: Reserve ~3–4 schedulers for the large tenant during churn; remaining schedulers shared across others.
- Partitions: Large = 64, medium = 32, small = 16. Tune based on contention and agenda behavior.
- Placement: Avoid co-locating multiple large tenants on the same node; rebalance when hotspots are detected.
Example B — Many small tenants on an 8-core, 32 GB node
- Tenants: ~80–120 small tenants (100k facts, 50–150 rules), engines started on demand.
- Memory: ~0.2 GB × 100 ≈ 20 GB for engines at peak; target < 60% steady-state via idle eviction.
- CPU: 8 schedulers suffice with modest concurrency; keep tracing off; enable limited sampling.
- Start-on-demand: Cold start budget < 1s using preloaded compiled networks and snapshots.
Example C — Heavy-rule tenants (500 rules) across cluster
- Spread tenants with 500 heavy rules evenly; their compile artifacts and predicate specialization increase CPU.
- Consider dedicating nodes with higher clocks; keep tracing disabled; tune fire limits to cap tail latency.