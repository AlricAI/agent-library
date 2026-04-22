---
name: Schema Registry
description: Purpose

- Define where and how domain types (e.g., TimesheetEntry, PayLine, Decision, ComplianceViolation) are declared, validated, and versioned for
model: claude-sonnet-4-5
---
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
          "end_at" => :datetime,
          "hours" => :float,
          "project_id" => :string,
          "cost_center" => :string,
          "approved?" => :boolean
        },
        meta: %{primary_keys: ["id"], indexes: ["employee_id", "start_at"]}
      },
      "PayRate" => %{
        fields: %{
          "id" => :string,
          "employee_id" => :string,
          "rate_type" => {:enum, [:hourly, :salary]},
          "base_rate" => :decimal,
          "effective_from" => :datetime,
          "effective_to" => :datetime
        },
        meta: %{indexes: ["employee_id", "effective_from"]}
      }
    }
  end

  @doc "Emit types: map of type name => %{fields, meta}."
  def emit_types do
    %{
      "Decision" => %{
        fields: %{
          "type" => :string,
          "employee_id" => :string,
          "overtime_hours" => :float,
          "rate" => :decimal
        },
        meta: %{}
      },
      "ComplianceViolation" => %{
        fields: %{
          "employee_id" => :string,
          "period_key" => :string,
          "code" => :string,
          "severity" => {:enum, [:low, :medium, :high]},
          "details" => :string
        },
        meta: %{}
      }
    }
  end
end
```

## Integration Points

- Parser: validate `type_name(field: ...)` against `fact_types/0`.
- Compiler: type-check operators; generate Alpha tests for known fields.
- Runtime: validate `emit` payloads against `emit_types/0` before queuing.

## Guarantees

- Registry lookups are total for declared types.
- Unknown types/fields raise validation errors (see `specs/parser_contract.md`).

## FAQ

- Where do I add a new domain type? Add to `Epona.Schemas` and update `specs/fact_schemas.md` if canonical.
- Multi-tenant variations? Introduce per-tenant overlays later via DB-backed schemas.
- Does the EBNF cover all domains? Yes: the grammar is domain-agnostic. Domain coverage comes from the registry; any type present in the registry is usable in the DSL.