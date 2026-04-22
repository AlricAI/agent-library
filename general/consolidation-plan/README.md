# Consolidation Plan

> **Created:** 2026-02-23  
**Updated:** 2026-03 (doc overhaul: ROADMAP/BASELINE/dated release docs removed; FOUNDATIONS_GOVERNANCE, TELEMETRY_OBSERVABI

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Documentation Consolidation & Unimplemented Tasks Plan

**Created:** 2026-02-23  
**Updated:** 2026-03 (doc overhaul: ROADMAP/BASELINE/dated release docs removed; FOUNDATIONS_GOVERNANCE, TELEMETRY_OBSERVABILITY_DATA_FLOW, SYSTEM_MAP, observability ARCHITECTURE/FOLDER_STRUCTURE/legacy-removal merged; OpenAPI path unified to openapi/openapi.yaml)
**Purpose:** Single place for doc structure, consolidation, and unimplemented work.

---

## 0. Consolidated guides (2026-02-24)

**Added:** `docs/guides/` — single entry points by persona.

| Guide | Path | Audience |
|-------|------|----------|
| Operations | [guides/operations-guide.md](guides/operations-guide.md) | Ops, SRE |
| Observability | [guides/observability-guide.md](guides/observability-guide.md) | Ops, SRE |
| Development | [guides/development-guide.md](guides/development-guide.md) | Developers |

Master index: [docs/README.md](README.md) — links to guides + full doc tree.

---

## 1. Current Documentation Map

### 1.1 Root (14 files) — DONE
| File | Topic | Action (done) |
|------|-------|--------|
| PROMPT.md | Multi-agent workflow | **Keep** (Cursor prompt) |
| README.md | Quick start | **Keep** |
| AGENTS.MD | Codex/agent instructions | **Keep** |
| CHANGELOG.md | Version history | **Keep** |
| RUNBOOK.md | Observability runbook | → docs/observability/runbook-observability.md |
| VALIDATION.md | Observability validation | → docs/observability/validation.md |
| DATA_CONTRACT.md | AWG data contract | → docs/observability/data-contract.md |
| BASELINE.md | Runtime snapshot | → docs/audits/baseline-capture-2026-02-22.md |
| SERVER_LOGS_REPORT.md | Audit | → docs/audits/SERVER_LOGS_REPORT.md |
| PERFORMANCE_BOTTLENECK_REPORT.md | Audit | → docs/audits/PERFORMANCE_BOTTLENECK_REPORT.md |
| SECURITY_RISK_REPORT.md | Audit | → docs/audits/SECURITY_RISK_REPORT.md |
| HARDENING_ACTION_PLAN.md | Security | → docs/security/hardening.md (done) |
| THREAT_MODEL.md | Security | → docs/security/threat-model.md (done) |
| I

*[truncated — see source for full prompt]*