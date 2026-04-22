# Requirements

> ## Project Overview

**Objective**: Build a production-ready orchestration service that generates benign telemetry to simulate ordinary Azure tenant o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker - Structured Requirements Document

## Project Overview

**Objective**: Build a production-ready orchestration service that generates benign telemetry to simulate ordinary Azure tenant operations using multiple service principals executing diverse administrative scenarios.

**Key Constraint**: All operations must adhere to Zero-BS Philosophy (no stubs, TODOs, faked APIs, or placeholder data).

---

## Non-Negotiable Requirements

### 1. Repository Setup
- GitHub repository: `rysweet/AzureHayMaker` (public, open source)
- Default branch: `main`
- Branch protection: PRs required for merging to main
- Auto-update PR branches when out of date
- Local git repository initialized at: `/Users/ryan/src/AzureHayMaker`

### 2. Technology Stack
- **Language**: Python
- **Package Manager**: uv
- **Testing**: pytest
- **Linting**: ruff
- **Type Checking**: pyright
- **Pre-commit Hooks**: Must enforce linting, formatting, type safety, and test execution

### 3. Azure Tools Required
- Azure CLI (az)
- Terraform
- Azure Bicep
- EntraID admin capabilities

### 4. External Dependencies
- Anthropic API (Claude Code)
- Azure Container Apps
- Azure Functions (for scheduling)
- Azure Event Bus (for agent logging)

---

## Phase 1: Groundwork - Scenario Creation

### Objective
Research Azure Architecture Center and create 50+ operational scenarios with corresponding goal-seeking agents.

### Requirements

#### 1.1 Claude Code Skill Development
**Source**: Azure Architecture Center (https://learn.microsoft.com/en-us/azure/architecture/)

**Deliverable**: Claude Code skill(s) with progressive disclosure that cover:
- All main Technology Areas from Azure Architecture Center
- Comprehensive documentation/knowledge of:
  - Azure CLI usage
  - Terraform on Azure
  - Azure Bicep
  - EntraID administration
- Installation instructions for all required tools
- Clear references to official documentation

**Acceptance Criteria**:
- [ ] Skill can answer questions about each Technology 

*[truncated — see source for full prompt]*