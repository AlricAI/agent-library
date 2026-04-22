# Schema Registry

> Purpose

- Define where and how domain types (e.g., TimesheetEntry, PayLine, Decision, ComplianceViolation) are declared, validated, and versioned for

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Schema Registry — Facts and Emits (v0)

Purpose

- Define where and how domain types (e.g., TimesheetEntry, PayLine, Decision, ComplianceViolation) are declared, validated, and versioned for the DSL and engine.

Scope

- Facts (inputs/WMEs) — see `specs/fact_schemas.md` for canonical shapes.
- Emits (outputs) — decision/derivation payloads emitted by rules.

## Storage Model

Start simple (BSSN): code-first registry loaded at boot, with optional DB persistence later.

### Code-first registry (default)

- File: `lib/epona/schemas.ex`
- Functions:
  - `fact_types/0 :: %{String.t() => %{fields: %{String.t() => type()}, meta: map()}}`
  - `emit_types/0 :: %{String.t() => %{fields: %{String.t() => type()}, meta: map()}}`
- Types: `:string | :integer | :float | :decimal | :boolean | :date | :datetime | {:enum, [atom()]} | {:ref, type_name}`
- Version: include `version()/0` returning a string (e.g., "v1").
- Use: Parser and compiler consult this module to validate identifiers and field types.

### Optional DB-backed (later)

- Tables: `fact_schemas`, `emit_schemas` (tenant_id, version, name, fields JSON, status, inserted_at).
- Cache: ETS per tenant/version; hot reload via PubSub.
- Export/Import: mirror to files under `priv/rules/{tenant}/{version}/schemas.json` for audit.

## Authoring Guidance

- Add/modify types in `Epona.Schemas` as Elixir maps.
- Keep names stable; changes require a new schema version.
- Prefer additive changes; avoid breaking field renames.

## Minimal Example (Elixir)

```elixir
# filepath: lib/epona/schemas.ex
# ...existing code...
defmodule Epona.Schemas do
  @moduledoc """
  Canonical domain schemas consulted by the DSL parser/compiler.
  """

  @doc "Return the schema registry version."
  def version, do: "v1"

  @doc "Fact types: map of type name => %{fields, meta}."
  def fact_types do
    %{
      "TimesheetEntry" => %{
        fields: %{
          "id" => :string,
          "employee_id" => :string,
          "start_at" => :datetime,
    

*[truncated — see source for full prompt]*