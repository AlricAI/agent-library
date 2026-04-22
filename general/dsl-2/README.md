# Dsl

> A textual, Elixir-agnostic DSL compiled to a RETE IR.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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

- Rule: `rule "name" [salience: int] do ...

*[truncated — see source for full prompt]*