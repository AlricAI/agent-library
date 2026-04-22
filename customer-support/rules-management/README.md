# Rules Management

> Defines the lifecycle of rulesets, support for shared bundles and tenant-specific overlays, and an LLM-assisted authoring flow.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Rules Management and Interactive Authoring

Defines the lifecycle of rulesets, support for shared bundles and tenant-specific overlays, and an LLM-assisted authoring flow.
Rationale — Prefer a DSL over plain structs

- Readable domain language for rules; less boilerplate.
- Strong compile-time validation and safer multi-tenant authoring.
- Better optimization opportunities (alpha keys, join ordering, node sharing).
- Deterministic semantics (agenda/refraction) and side-effect-free conditions.
- Text-based artifacts enable diff/review/audit and LLM-assisted workflows; portable across the gRPC boundary.

## Ruleset Model

- Identity: `{tenant_id :: String.t(), ruleset_id, version}`; versions are immutable once compiled.
- Composition: `ruleset = shared_bundle(:id) + tenant_overlay(:id)` with conflict resolution (tenant overlay wins).
- Metadata: tags, groups, salience defaults, change log, owner.

## Lifecycle

1. Define: Create/update DSL sources for shared and tenant overlays.
2. Validate: Static checks (schema/types/guards) and simulation on sample facts.
3. Compile: Produce a shared network and predicate modules; store artifacts in cache/storage.
4. Activate: Mark a version active and notify engines; engines switch atomically at agenda-safe points.
5. Retire/Rollback: Deactivate older versions; retain for audit.

## Dynamic Use with Facts

- Facts may include `ruleset_version` to assert alignment; otherwise the engine uses its current active ruleset.
- There is no conversion at ingest time; rules are precompiled; activation is a control-plane action, not per-fact.

## Interactive Authoring (LLM-Assisted)

- Flow: Natural language → draft DSL → validate → simulate → review → compile → activate.
- Guardrails:
  - Strict schema and predicate whitelist; no arbitrary code execution.
  - Automated tests generated from the NL spec (examples, counterexamples) to validate semantics.
  - Provenance: Store NL prompt, generated DSL diff, and review approvals.
- UX Guideline

*[truncated — see source for full prompt]*