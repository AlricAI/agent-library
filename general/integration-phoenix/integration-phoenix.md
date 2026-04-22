---
name: Integration Phoenix
description: This Phoenix application encapsulates the Epona rules engine and an interactive UI for authoring rules.
model: claude-sonnet-4-5
---
# Phoenix Integration — App + gRPC

This Phoenix application encapsulates the Epona rules engine and an interactive UI for authoring rules. External applications integrate over a gRPC API exposed by this app. Runs on a private network; AuthN/AuthZ not required. Optionally enable mTLS for channel security. No app-level auth in scope.

## Integration Model

- Embedding: Epona runs in-process within the Phoenix app.
- External Interface: A gRPC server exposes engine and rules management operations to other applications.
- Ownership: The Phoenix app owns tenants (identified by a single string ID), storage, and the ruleset control plane (define/validate/compile/activate).
- UI/LLM: The interactive ruleset builder UI and LLM pipelines live in this Phoenix app and call local Epona modules.

## Supervision & Contexts

- Supervision
  - `Epona.Supervisor` runs inside the Phoenix supervision tree.
  - `TenantEngineSupervisor` starts/stops per-tenant engines (keyed by `tenant_id :: String.t()`).
  - `GrpcServerSupervisor` starts the gRPC server endpoints for engine and rules services.
- Phoenix Contexts (suggested)
  - `Rules` context: CRUD for rulesets, validation, compilation, activation, audit trail.
  - `Engines` context: Lifecycle of per-tenant engines; start/stop, set ruleset, stats.
  - `LLM` context: Prompting, draft generation, alignment, and guardrails.

## Typical Flows

- Author → Validate → Compile → Activate
  1. Authoring (LLM-assisted): NL spec → draft DSL (never executed directly).
  2. Validation: static checks + simulation with representative facts (no engine mutation).
  3. Compilation: produce compiled network artifacts; cache by `{tenant, ruleset_id, version}`.
  4. Activation: call `Epona.Engine.set_ruleset/2` (or orchestrator) at agenda-safe boundary; broadcast UI updates.
- Data Ingest
  - External apps call gRPC `Assert/Modify/Retract` against a tenant ID to drive engines.
  - For bulk loads, prefer streaming gRPC or batched calls; set `bulk: true` on requests when supported.

## Storage

- Rulesets
  - Store DSL sources in DB (e.g., Postgres) with versions; compiled artifacts on disk or blob store, indexed by content hash.
  - Maintain a ruleset table: `{tenant, ruleset_id, version, status, active_at, compiled_at, artifact_path, checksum}`.
- Facts & Snapshots
  - Facts are transient (in-memory via ETS) unless you opt-in to persistence. Use snapshot APIs for fast restarts.

## LLM Guardrails

- PII redaction in prompts; clear scoping to a tenant’s schemas/predicates.
- Deterministic compilation path with strict schema checking; no dynamic code evaluation.
- Auto-generate tests from NL spec and require human approval before activation.

## Multi-Tenancy

- One engine per tenant (tenants are identified by a single string ID).
- Keep compiled shared bundles in memory; overlay tenant-specific rules and compile merged networks.

## Monitoring

- Collect per-tenant engine stats and expose Phoenix LiveDashboard cards: WM count, agenda length, fires/sec, memory usage.
- Issue backpressure responses in the app layer when memory budgets are exceeded.

## Example Wiring (Skeleton)

```elixir
# in your Phoenix app Application.start/2
children = [
  Epona.Application, # starts Registry and EngineSupervisor
  GrpcServerSupervisor # starts gRPC endpoints for EngineService/RulesService
]
# start a tenant engine (locally)
tenant_id = "acme"
{:ok, _pid} = Epona.start_engine(tenant_id, %Epona.Network{version: 1}, partitions: 32)
# set active ruleset after compile
:ok = Epona.Engine.set_ruleset(Epona.via(tenant_id), {"payroll", "v12"})
# external ingestion happens via gRPC; internal modules can call directly if needed
:ok = Epona.Engine.assert(Epona.via(tenant_id), %{id: "t1", employee_id: "e1", type: "TimesheetEntry"})
```

## Why This Approach

- Single deployable app that provides both UI and engine.
- gRPC boundary enables other services to integrate cleanly.
- Scales horizontally by running more Phoenix nodes; each hosts N tenant engines within memory/CPU budgets.