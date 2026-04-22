# Api

> Defines the application’s public interfaces: local Elixir APIs for internal use and gRPC services for external applications.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Public API Specification (Draft)

Defines the application’s public interfaces: local Elixir APIs for internal use and gRPC services for external applications.
Runs on a private network; AuthN/AuthZ not required. Optionally enable mTLS for transport security.
No app-level auth in scope.

## Engine Lifecycle (Local Elixir)

- `compile(rules, opts) :: {:ok, network} | {:error, reason}` — Build a shared network from DSL rules.
- `start_link(network, opts) :: GenServer.on_start()` — Start an engine instance.
- `stop(engine) :: :ok` — Stop the engine.
- `set_ruleset(engine, ruleset_id | {ruleset_id, version}) :: :ok` — Atomically switch engine to a compiled ruleset.

## Fact Operations (Local Elixir)

- `assert(engine, fact | [fact], opts) :: :ok | {:ok, result}`
- `modify(engine, fact | [fact], opts) :: :ok | {:ok, result}` — Fact `id` must match existing; engine diffs old/new.
- `retract(engine, id | [id], opts) :: :ok | {:ok, result}`
- `transact(engine, fun) :: {:ok, result} | {:error, reason}` — Run multiple ops as one batch.
- Options:
  - `return: :none | :activations | :derived` — What to return per op.
  - `trace_id: term` — Correlate operations to traces.
  - `partition_key: term` — Optional explicit routing key for operations (otherwise derived from fact fields).
  - `bulk: true` — Engage bulk-load mode (deferred agenda) for initial ingestion.
  - `ruleset_version: term` — Optional assertion that facts were produced against a specific ruleset version.

## Subscriptions (Local Elixir)

- `subscribe(engine, topic, opts)` — Topics: `:derived`, `{:derived, Module}`, `:activations`, `:trace`.
- `unsubscribe(engine, ref)`.

## Configuration (Local Elixir)

- `set_agenda_policy(engine, policy_module | :default)`.
- `set_refraction(engine, mode)`.
- `configure_tracing(engine, level | filter)`.
- `set_partitions(engine, n :: pos_integer)` — Configure internal partition count (applies on fresh engine).
- `set_memory_budget(engine, bytes)` — Soft cap for WM/memory; engi

*[truncated — see source for full prompt]*