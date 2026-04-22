# Integration Phoenix

> This Phoenix application encapsulates the Epona rules engine and an interactive UI for authoring rules.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
  - For bulk loads, prefer streaming gRPC or batched calls; set `bulk: true` on

*[truncated — see source for full prompt]*