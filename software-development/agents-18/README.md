# AGENTS

> This document explains the purpose, usage, and modification patterns for the
scripts/ folder. It is written for human developers and AI agents.

Note:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scripts (scripts/) — AGENTS Guide

This document explains the purpose, usage, and modification patterns for the
scripts/ folder. It is written for human developers and AI agents.

Note: scripts/bosun/ has its own documentation and is intentionally
excluded from this guide. See scripts/bosun/AGENTS.md.

## Module Overview
- Purpose: operational automation, build helpers, migrations, and one-off
  utilities that are not part of the main application runtime.
- Use when: you need to bootstrap environments, run localnet, generate
  artifacts, validate ops procedures, or automate workflows.
- Key entry points:
  - scripts/AGENTS.md:1
  - scripts/agent-preflight.ps1:1
  - scripts/agent-preflight.sh:1
  - scripts/localnet.sh:1
  - scripts/validate-agents-docs.mjs:1

## Architecture
- Top-level scripts focus on common workflows (localnet, chain init, inference
  checks, agent tooling).
- Subfolders group domain-specific automation:
  - scripts/compliance/ (SOC2 evidence collection)
  - scripts/dev/ (ad-hoc, task-specific helpers; often hard-coded paths)
  - scripts/dr/ (disaster recovery automation)
  - scripts/hpc/ (HPC proto bootstrap helpers and temp proto sources)
  - scripts/mainnet/ (genesis ceremony and launch validation)
  - scripts/rollback/ (operational rollback helpers)
  - scripts/supply-chain/ (dependency and SBOM tooling)
  - scripts/waldur/ (data artifacts used by ops scripts)

## Core Concepts
- Scripts are categorized by audience (ops vs dev vs automation) and platform
  (bash, PowerShell, Go, Node).
- Naming conventions are verb-first and kebab-case; internal helpers begin with
  an underscore.
- Prefer extending existing scripts when the workflow already exists; add new
  scripts when the change would make existing scripts harder to reason about.

## Usage Examples

### Pre-flight checks before push
`ash
pwsh scripts/agent-preflight.ps1
`

### Localnet orchestration
`ash
./scripts/localnet.sh start
`

### Generate API types
`ash
./scripts/generate-api

*[truncated — see source for full prompt]*