# Rulesets

> Goal

- Allow constructing rulesets in the UI by combining tenant-specific rules with rules created from global rule templates (read-only templates us

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
- File export (optional): `priv/rules/{tenant}/{r

*[truncated — see source for full prompt]*