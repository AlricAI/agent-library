# GETTING STARTED 129 CIRCUIT BREAKERS

> **Your complete guide to implementing Issue #129**

**Priority**: P1-High | **Effort**: 2 weeks | **ROI**: 150%

---

## What You're Building

Impleme

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started: Agent Health Checks and Circuit Breakers (Issue #129)

**Your complete guide to implementing Issue #129**

**Priority**: P1-High | **Effort**: 2 weeks | **ROI**: 150%

---

## What You're Building

Implement health checks, circuit breakers, and automatic recovery to prevent cascading failures when agents fail. Stop wasting resources on stuck/zombie agents.

**Why It Matters**: Production systems need resilience. One failing agent shouldn't bring down the entire system.

**Business Value**: Reduces MTTR from hours to minutes, prevents resource waste from stuck agents.

---

## Before You Start (15 minutes)

### 1. Understand Circuit Breaker Pattern

**Resources**:
- Circuit Breaker Pattern: https://martinfowler.com/bliki/CircuitBreaker.html
- Azure SDK resilience: Built into most Azure libraries

### 2. Check Dependencies

```bash
# Verify you have the pybreaker library available or will install it
grep -i "pybreaker\|circuitbreaker" pyproject.toml || echo "Need to add to pyproject.toml"
```

### 3. Review Current Agent Structure

```bash
# Understand how agents currently execute
ls -la src/azure_haymaker/agents/
find src -name "*.py" -path "*/agents/*" | head -10
```

---

## Phase 1: Set Up Structure (Day 1, ~3 hours)

### Create Branch
```bash
git checkout main
git pull origin main
git checkout -b feat/issue-129-circuit-breakers
```

### Create Directory Structure
```bash
mkdir -p src/azure_haymaker/orchestrator/health
touch src/azure_haymaker/orchestrator/health/__init__.py
touch src/azure_haymaker/orchestrator/health/circuit_breaker.py
touch src/azure_haymaker/orchestrator/health/health_monitor.py
touch src/azure_haymaker/orchestrator/health/models.py
```

### Add Dependencies
```bash
# Add to pyproject.toml [project.dependencies]
# pybreaker = "^0.7.0"

uv sync
```

### Create Health Models

**File**: `src/azure_haymaker/orchestrator/health/models.py`

```python
from pydantic import BaseModel
from datetime import datetime
from typing import L

*[truncated — see source for full prompt]*