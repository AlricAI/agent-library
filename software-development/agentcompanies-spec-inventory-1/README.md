# AGENTCOMPANIES SPEC INVENTORY

> This document indexes every part of the Paperclip codebase that touches the [Agent Companies Specification](docs/companies/companies-spec.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Companies Spec Inventory

This document indexes every part of the Paperclip codebase that touches the [Agent Companies Specification](docs/companies/companies-spec.md) (`agentcompanies/v1-draft`).

Use it when you need to:

1. **Update the spec** — know which implementation code must change in lockstep.
2. **Change code that involves the spec** — find all related files quickly.
3. **Keep things aligned** — audit whether implementation matches the spec.

---

## 1. Specification & Design Documents

| File | Role |
|---|---|
| `docs/companies/companies-spec.md` | **Normative spec** — defines the markdown-first package format (COMPANY.md, TEAM.md, AGENTS.md, PROJECT.md, TASK.md, SKILL.md), reserved files, frontmatter schemas, and vendor extension conventions (`.paperclip.yaml`). |
| `doc/plans/2026-03-13-company-import-export-v2.md` | Implementation plan for the markdown-first package model cutover — phases, API changes, UI plan, and rollout strategy. |
| `doc/SPEC-implementation.md` | V1 implementation contract; references the portability system and `.paperclip.yaml` sidecar format. |
| `docs/specs/cliphub-plan.md` | Earlier blueprint bundle plan; partially superseded by the markdown-first spec (noted in the v2 plan). |
| `doc/plans/2026-02-16-module-system.md` | Module system plan; JSON-only company template sections superseded by the markdown-first model. |
| `doc/plans/2026-03-14-skills-ui-product-plan.md` | Skills UI plan; references portable skill files and `.paperclip.yaml`. |
| `doc/plans/2026-03-14-adapter-skill-sync-rollout.md` | Adapter skill sync rollout; companion to the v2 import/export plan. |

## 2. Shared Types & Validators

These define the contract between server, CLI, and UI.

| File | What it defines |
|---|---|
| `packages/shared/src/types/company-portability.ts` | TypeScript interfaces: `CompanyPortabilityManifest`, `CompanyPortabilityFileEntry`, `CompanyPortabilityEnvInput`, export/import/preview request and result types, manifest entry 

*[truncated — see source for full prompt]*