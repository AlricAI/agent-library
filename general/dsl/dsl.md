---
name: Dsl
description: A textual, Elixir-agnostic DSL compiled to a RETE IR.
model: claude-sonnet-4-5
---
# Rule DSL Specification (Textual DSL + IR)

A textual, Elixir-agnostic DSL compiled to a RETE IR. Author in DSL text (see `specs/dsl_ebnf.md`); engine executes compiled JSON IR (`specs/ir.schema.json`). No dynamic Elixir eval.

## Why a DSL (vs plain structs)

- Expressive domain language: Rules read as high-level intent (patterns, joins, not/exists, accumulate) instead of low-level data plumbing.
- Compile-time validation: Field names, schemas, guard purity, and deterministic constructs are checked before runtime with precise errors.
- Safety by design: Declarative constraints avoid arbitrary user code; safer for multi-tenant authoring, storage, and gRPC transmission.
- Optimizable plan: Compiler can choose alpha keys, join order, and share nodes; enables constant folding and predicate specialization for performance.
- Determinism: Enforces reproducible semantics (agenda/refraction) and disallows side effects inside conditions.
- Abstractions & reuse: Macros/helpers for common patterns reduce boilerplate and drift across large rulesets.
- Tooling & audit: Text artifacts are easy to diff, lint, document, review, and roll back with approvals.
- LLM-assisted authoring: Enables NL → DSL workflows with validation; mapping NL to arbitrary structs is harder to verify.
- Cross-boundary portability: DSL text/AST transmits cleanly over gRPC and compiles deterministically per tenant.
- Performance headroom: Supports partial evaluation and optional codegen of hot predicates for faster networks.
- Guardrails at scale: Consistent rule semantics across 100 tenant engines; fewer runtime surprises than ad-hoc struct encodings.
Pragmatic approach
- DSL → IR: Compile DSL to a validated internal IR/struct the engine executes.
- Escape hatches: Allow vetted predicate modules behind feature flags for rare cases.
- Strict by default: Keep the public/gRPC surface declarative; reserve imperative hooks for trusted internal code paths.

## Basics

- Rule: `rule "name" [salience: int] do ... end`
- LHS (when): `when` block with patterns and `guard ...` lines.
- RHS (then): `then` block with `emit Type(field: value, ...)` actions.
- Full grammar: `specs/dsl_ebnf.md`; examples: `specs/dsl_examples.md`.

## Namespacing and Sharing

- Rules belong to a ruleset identified by `{tenant_id :: String.t(), ruleset_id, version}`.
- Shared Bundles: Rules can be published into a shared bundle; tenant rulesets declare `use shared: :bundle_id` to compose.
- Import Controls: Explicit imports of predicates/helpers from whitelisted modules; no dynamic `Code.eval_string`.

## Patterns

- Syntax: `TypeName(field1: value_or_var, field2: value_or_var, ...)` optionally bound as `alias: TypeName(...)`.
- Bindings: Simple identifiers (e.g., `e`, `h`); constants are literals (strings, numbers, bools, dates) or enums.
- Guards: `guard <expr>` using the DSL operators (==, !=, >, >=, <, <=, in, not_in, between, and/or).
- Negation/Existence: v0 uses guards and joins; explicit `not`/`exists` may be added later as extensions.

### Examples (see `specs/dsl_examples.md` for more)

```dsl
rule "base-pay" salience: 100 do
  when
    ts: TimesheetEntry(employee_id: e, start_at: s, end_at: f, approved?: true)
    rate: PayRate(employee_id: e, rate_type: :hourly, base_rate: r)
    guard hours_between(s, f) > 0
  then
    emit PayLine(employee_id: e, period_key: bucket(:week, s), component: :base,
                 hours: hours_between(s, f), rate: r,
                 amount: r * hours_between(s, f))
end
```

## Joins

- Joins occur via shared variables (e.g., `?e` across patterns) and guard comparisons (e.g., `?x.id == ?y.customer_id`).

## Negation and Existence

- Future extension. In v0, express negatives via guards (e.g., `guard not (cond)`) and by absence checks using precomputed facts.

## Accumulation (deferred)

- Planned extension for v1.x. For now, represent aggregates as precomputed facts (e.g., `WeeklyHours`) and join/guard against them.

## Actions

- `emit Module, key: val, ...` creates a derived fact for downstream rules or subscribers.
- `call Module.function(args...)` executes a side-effect under Engine control (use sparingly; prefer emits).
- `log level, message` records trace messages.

## Metadata

- `salience: integer` controls agenda priority.
- `tags: [atoms]` user-defined labels.
- `refraction: :default | :none | :custom` policy overrides.
- `scope: :tenant | :shared` — Marks whether a rule is tenant-specific or part of a shared bundle.
- `group: atom` — Logical grouping for large rulesets; aids UI organization.

## Compilation Guarantees

- Pattern ordering may be optimized; semantics preserved.
- Alpha tests reordered by selectivity; Beta joins planned left-to-right based on bound variables.
- Guards compiled to predicates executed at nodes to prune early.