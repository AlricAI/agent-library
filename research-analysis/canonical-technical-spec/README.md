# CANONICAL TECHNICAL SPEC

> ## 1. Repository Analysis (Concise)

- The repository is implemented as a FastAPI-based AI platform with explicit backend/frontend separation under `s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AETHERIUM-GENESIS Canonical Technical Specification

## 1. Repository Analysis (Concise)

- The repository is implemented as a FastAPI-based AI platform with explicit backend/frontend separation under `src/backend` and `src/frontend`.
- Runtime control and orchestration are backend-first: `src/backend/main.py` initializes bus, cognition engine, governance, entropy/memory services, routers, and static serving.
- Core architecture is present in code as subsystem modules:
  - Reasoning (Logenesis + agents)
  - Governance (risk tiering, approval routing)
  - Bus (AetherBus event transport)
  - Execution adapters (vessels)
  - Memory (Akashic ledger and projections)
  - Frontend manifestation surfaces (PWA/dashboard/GunUI pages)
- Protocol surfaces are strongly schema-oriented (Pydantic models and JSON schema), though mixed generation-era docs include both canonical and legacy language.

## 2. System Purpose

AETHERIUM-GENESIS is an AI Operating System platform that converts human/system intent into governed, auditable action and manifests resulting state to operators.

Canonical operational loop:

`Intent -> Reasoning -> Policy Validation -> Execution -> Memory Commit -> Manifestation`

The platform goal is deterministic, inspectable, and replayable operation across internal cognition, governance controls, execution adapters, and human-facing manifestation.

## 3. Architectural Scope

### 3.1 In Scope

- **Mind (Reasoning):** intent interpretation and response synthesis (`logenesis`, cognitive agents).
- **Kernel (Governance):** policy/risk tiering, approvals, and enforcement gates.
- **Bus (Transport):** explicit event envelope transport across components.
- **Hands (Execution):** vessels/adapters for external actions.
- **Memory (Continuity):** append-only records and derived projections.
- **Body (Manifestation):** frontend rendering of state/directives.

### 3.2 Out of Scope

- Frontend-authored cognition or policy decisions.
- Unvalidated action execution paths b

*[truncated — see source for full prompt]*