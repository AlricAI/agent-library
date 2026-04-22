---
name: Orchestrator
description: Describes how 1000 concurrent tenant engines run with isolation and fairness.
model: claude-sonnet-4-5
---
# Connection Orchestrator & Deployment Topology

Describes how 1000 concurrent tenant engines run with isolation and fairness.

## Supervision Topology (Per Node)

```mermaid
flowchart TB
  Root[Epona.Application]
  Root --> PS[PartitionSupervisor Epona.Partitions]
  PS --> DS0[DynamicSupervisor p0]
  PS --> DS1[DynamicSupervisor p1]
  PS --> DSn[DynamicSupervisor pN]
  DS0 --> EngA[Epona.Engine (tenant A)]
  DS1 --> EngB[Epona.Engine (tenant B)]
```

- `Epona.Application` (root)
  - `Registry` — `:via` names for engines
  - `DynamicSupervisor` — starts/stops `Epona.Engine` per tenant (`tenant_id :: String.t()`)

## Engine Structure (Per Tenant)

```mermaid
flowchart TB
  subgraph Eng[Epona.Engine (tenant)]
    ORCH[Orchestrator]
    P0[Partition 0]
    P1[Partition 1]
    PN[Partition N]
  end
  ORCH --> P0
  ORCH --> P1
  ORCH --> PN
  P0 --> ORCH
  P1 --> ORCH
  PN --> ORCH
```

- `Epona.Engine` — orchestrator GenServer
  - N x `Epona.Partition` — partition processes (16–64)
  - Optional Tracer and Metrics reporters (off by default in prod)
  - Active Ruleset: `{ruleset_id, version}`; orchestrator coordinates atomic ruleset switches across partitions.
Engine holds the immutable compiled network (in `persistent_term`) and routes deltas by partition key. Partitions maintain ETS tables for WM, Alpha, and Beta memories.
gRPC requests are stateless and routed by `tenant_id` to the correct engine instance via `Registry`. `tenant_id` (single string) is the leading key for process names (`via(tenant_id)`), partition routing, caches, snapshots, and telemetry.

## Routing and Fairness

```mermaid
flowchart LR
  Key[tenant_id or dominant key] --> H[hash(key) mod N]
  H --> P0
  H --> P1
  H --> PN
```

- Route `assert/modify/retract` by partition key (e.g., `employee_id` hash)
- Round-robin partitions when draining agenda to prevent starvation
- Cap fires per tick per partition to bound latency during bursts
- Ruleset Switch: Pause agenda briefly to swap networks; complete in-flight batches on old version before resume.

## Engine Pooling and On-Demand Start

- Idle Eviction: Stop idle tenant engines after a configurable idle time; persist snapshot and metrics.
- Start on Demand: gRPC requests for an evicted tenant trigger engine startup and snapshot restore.
- Preload Artifacts: Keep compiled networks in a shared cache to minimize cold start time.

## Placement and Scheduling

- Placement Strategy: Distribute large tenants across nodes; pack small tenants to improve utilization.
- Multi-Node Registry: Use a cluster-aware registry (e.g., via Horde/SWARM or custom) to route `tenant_id` to node-local engines.
- Backpressure Policy: Apply per-tenant fire limits and global node limits; respond with RESOURCE_EXHAUSTED over gRPC when saturated.

## Backpressure and Limits

- Per-tenant limits: Memory budgets (WMEs, alpha/beta memories) and per-tick fire caps enforced at the engine level.
- Node/global limits: Admission control when CPU/memory pressure rises; throttle agenda draining globally.
- Signals to clients: See specs/api.md and specs/grpc.md for error signaling (`{:error, :resource_exhausted}` locally, `RESOURCE_EXHAUSTED` over gRPC) and client backoff guidance.
- Operational knobs: Fire-limit per partition, max agenda depth, snapshot-on-idle thresholds, eviction grace period, and per-tenant quotas are tunable.

## Deployment Patterns

- Single Node: Up to the machine’s memory/CPU budget; pin max engines accordingly
- Small Cluster: Spread engines across nodes; keep each tenant engine local to a node
- Persistence: Store snapshots per tenant; restore onto any node

## Operational Defaults

- Tracing disabled; sample <= 1% when enabled
- Backpressure when memory budget reached per engine
- Bulk-load mode for initial 1–2M fact ingestion; then switch to incremental