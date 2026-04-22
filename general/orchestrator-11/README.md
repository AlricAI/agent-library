# Orchestrator

> Describes how 1000 concurrent tenant engines run with isolation and fairness.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
- Ruleset Switch: Pause agenda briefly to swap networks; complete 

*[truncated — see source for full prompt]*