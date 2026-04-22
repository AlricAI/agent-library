# Performance Targets

> High-level performance targets for Epona.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Performance Targets

High-level performance targets for Epona. Update with measured results as the implementation matures. BSSN: keep targets simple, speed-first.

## Measurement Protocol

- Build: `MIX_ENV=prod` with code paths warmed; tracing disabled
- Input: deterministic seed datasets (payroll, compliance, estimation)
- Runs: warm-up once, then N measured runs; report p50/p95
- Metrics: total time, facts/sec, memory RSS, ETS sizes; cores used
- Environment: record CPU model, cores, RAM, Erlang/Elixir versions

## Baseline Targets (single tenant)

- Simple filter (1 rule):
  - 100K facts ≤ 150ms
  - 200K facts ≤ 300ms
  - 500K facts ≤ 800ms
  - 1M facts ≤ 2.0s
  - 2M facts ≤ 5.0s
- Payroll (4–8 rules, weekly bucket + overtime):
  - 100K facts ≤ 250ms
  - 500K facts ≤ 1.2s
  - 1M facts ≤ 2.5s
- Enterprise mix (250–500 rules):
  - 250K facts ≤ 1.5s
  - 500K facts ≤ 3.5s
  - 1M facts ≤ 7.5s
  - 2M facts ≤ 16s
- Memory envelope (in-memory backend, includes WM/alpha/beta/agenda):
  - 1M facts ≤ 2.0 GB
  - 2M facts ≤ 4.5 GB

## Multi-Tenant Targets (clustered)

- Concurrent engines: 1000 tenants active (mixed sizes)
- Tail latency: p95 propagation for small deltas (≤ 100 facts) < 1s per tenant
- Cold start: < 1s to accept ingest using compiled network + snapshot restore
- Idle eviction + restore: snapshot save < 3s; restore < 1s

## Scaling Characteristics (expected)

- Near-linear with fact count for simple rules
- Throughput decreases with rule count but remains stable under backpressure
- Parallelism: partitions = 16–64 per engine; aligns with schedulers

## Optimisation Levers

- Alpha key selection and predicate ordering (compiler)
- Hash-join keys and beta memory indexing
- Accumulate reducer choice and Kahan optionality
- Refraction TTL and exact vs approximate (off by default)
- Batch size tuning and bulk-load mode for initial ingest

## Reporting Format (to be filled with measured results)

| Scenario | Facts | Rules | p50 | p95 | RSS | Facts/sec |
|-------

*[truncated — see source for full prompt]*