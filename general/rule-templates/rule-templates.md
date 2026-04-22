---
name: Rule Templates
description: Purpose

- Provide globally managed starting points for rules that tenants can materialise into their own editable rules.
- Templates are read-only to
model: claude-sonnet-4-5
---
# Rule Templates (v0)

Purpose

- Provide globally managed starting points for rules that tenants can materialise into their own editable rules.
- Templates are read-only to tenants; updating a template does not mutate existing tenant rules derived from it.

## Concepts

- Template: Named, versioned DSL source with optional attributes for discovery (e.g., {"country":"US","org_type":"hospital"}).
- Materialisation: Creating a new tenant rule by copying a template's DSL into a tenant-owned rule record; provenance is retained via `template_id` and template version in the rule's metadata.

## Storage

- `rule_templates`
  - id (uuid), name (string), version (string), status (draft|active|archived)
  - attrs jsonb (free-form tags for search and grouping)
  - template_dsl (text)
  - checksum (sha256 of normalised DSL)
  - created_at, updated_at

- `rules` additions (see `specs/rulesets.md`)
  - template_id (nullable uuid)
  - initial_prompt (text), llm_prompt (text), llm_model (string), generated_by (string)

## Authoring & Versioning

- Templates are created and edited by global admins only.
- Publishing a template creates a new immutable version.
- Tenants discover templates via search/filter on `attrs` and `name`.

## Materialisation Flow (UI/API)

1) Tenant selects a template → preview DSL and description.
2) Click "Create from template" → creates a tenant rule with:
   - source_dsl copied from template_dsl
   - template_id set to the template record and captured template version
   - status set to draft
3) Tenant may edit the new rule's DSL before adding to a ruleset.
4) On publish of the ruleset, that rule version is frozen in the manifest.

## LLM Provenance

- When creating or editing rules via LLM:
  - Store `initial_prompt` (user text)
  - Store `llm_prompt` (the revised/system-enriched prompt the model used)
  - Store `llm_model` and `generated_by` (e.g., user id or automation)
- Read APIs MUST omit prompt fields by default. Provide an explicit `include_prompts=true` flag for admin-only endpoints.

## Internal operations (contexts)

- Templates (admin-only operations)
  - Templates.create_template(attrs)
  - Templates.update_template(template, attrs)  # draft only
  - Templates.publish_template(template)        # creates new version
  - Templates.search_templates(filters)         # by name/attrs
  - Templates.get_template!(id)

- Rules (tenant operations)
  - Rules.materialise_from_template(template_id, tenant_id, attrs)
  - Rules.get_rule!(tenant_id, id, opts \\ [])   # opts: include_prompts?: false
  - Rules.update_rule(rule, attrs)
  - Rules.delete_rule(rule)

## Determinism & Audit

- Keep checksums for both template_dsl and rule source_dsl.
- Record template version in the rule metadata at materialisation time.
- Ruleset manifest should include rule ids/versions; no need to track template versions there.

## Notes

- BSSN: No template dependencies or inheritance in v0. Each template is a flat rule source.
- Future: Template bundles (collections of templates) can be added if needed.