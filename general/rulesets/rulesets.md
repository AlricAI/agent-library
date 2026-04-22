---
name: Rulesets
description: Goal

- Allow constructing rulesets in the UI by combining tenant-specific rules with rules created from global rule templates (read-only templates us
model: claude-sonnet-4-5
---
# Rulesets, Tenants, and General Rules (v0)

Goal

- Allow constructing rulesets in the UI by combining tenant-specific rules with rules created from global rule templates (read-only templates used to materialise tenant rules).

Definitions

- Rule Template: A globally managed DSL template used to create tenant rules; templates are read-only to tenants and versioned.
- Rule: A tenant-owned rule (source) created either from scratch or materialised from a template; stored and versioned per tenant.
- Ruleset: An ordered collection of rule references used by an engine instance.

Model

- Rule templates are curated globally and versioned.
- Tenants create rulesets which include only tenant rules. Tenant rules may be created from templates (materialised copy) or authored from scratch.
- Templates are read-only; updating a template does not change existing tenant rules that were created from it.

Persistence (DB-first, file export optional)

- tables:
  - `rule_templates` (id, name, version, status, attrs jsonb, template_dsl text, checksum, created_at, updated_at)
  - `rules` (id, tenant_id, name, version, status: draft|active|archived, source_dsl text, compiled_ir jsonb, checksum, created_at, updated_at,
     initial_prompt text, llm_prompt text, llm_model text, generated_by text, template_id nullable)
  - `rulesets` (id, tenant_id, name, status, version, meta jsonb, created_at, updated_at)
  - `ruleset_rules` (id, ruleset_id, ref_rule_id, position, pinned_version?, created_at, updated_at)
- Notes:
  - Rule templates are global authoring artefacts used to materialise tenant rules; once materialised, rules are independent from their template.
  - attrs is an open key/value map for tags (e.g., {"country":"US","state":"CA","city":"SF","org_type":"hospital"}).
  - Store LLM provenance on rules: initial_prompt (user text), llm_prompt (revised/clarified), llm_model, generated_by. Prompts are NOT returned by default in read APIs.
- File export (optional): `priv/rules/{tenant}/{ruleset_version}/compiled.ir.json` (merged IR), plus `source.dsl` and a manifest of component rule versions.

UI Behaviour

- Ruleset Builder page:
  - Add tenant rule (new or existing)
  - Create from template: pick a rule template → preview → materialise a tenant rule (becomes editable copy)
  - Reorder rules (defines salience groups or ordering hints)
  - Publish ruleset → compiles and freezes rule versions
- Templates appear read-only (badge: Template). Materialised rules show provenance (Template@Version) and attrs on hover.
- Tenant rules support edit, duplicate, archive.
- Only global admins can edit rule templates and publish template versions.

Compilation & Merging

- Input: tenant_id, ruleset_id, selected versions.
- Process:
  1) Load active tenant rules referenced by the ruleset.
  2) Parse/validate each rule's DSL source to AST (per `parser_contract.md`).
  3) Compile each to IR fragments (rules + network subgraphs).
  4) Merge:
     - Effective ruleset = union of tenant rules (some may have provenance to templates, but all are tenant-owned).
     - Union rules; fail on duplicate rule ids within the ruleset.
     - Merge alpha/beta nodes by structural equivalence (hash of tests).
     - Agenda combines activations; salience preserved; optional offset per rule order.
  5) Emit merged IR (conforms to `specs/ir.schema.json`).
  6) Persist compiled ruleset IR with `ruleset_version` and a manifest of component rule versions.
- Determinism: same inputs → same merged IR checksum.
- Override guidance: to supersede a prior rule, use a new id and higher salience or narrowed guards; duplicate ids are rejected.

Orchestrator Loading

- Engine key: {tenant_id, ruleset_version}.
- On start or cache miss:
  - Fetch compiled ruleset IR
  - Instantiate RETE network
- On publish of new ruleset version:
  - Hot-swap engine to new IR; old kept for in-flight processing if needed.

Governance & Rollouts

- General rule change creates a new general bundle version.
- Tenants referencing “latest” can opt-in automatically, or rulesets can pin specific versions.
- Changing a general rule does not mutate existing compiled rulesets; tenants must republish or auto-advance according to policy.

Internal operations (contexts)

- Admin (global): manage templates; publish template versions.
- Tenant: CRUD tenant rules, assemble rulesets, publish ruleset.
- Validation: Prevent inclusion of conflicting rule ids in a ruleset.

Read-only Enforcement

- UI: disable editing controls for general rules; show provenance (bundle@version).
- Server: reject updates when `tenant_id` is null (general rule) except by global admins.

Tests

- Unit: merging determinism, id conflicts, salience preservation.
- Integration: publish ruleset with mix of general + tenant rules, verify engine loads and fires.

Notes

- BSSN: start with single global bundle type; extend to multiple bundles later.
- Salience strategy: either encoded per-rule or derive from ruleset ordering; keep simple in v0.