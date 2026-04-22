# GETTING STARTED 128 COST ENFORCEMENT

> **Your complete guide to implementing Issue #128**

**Priority**: P1-High | **Effort**: 1.5 weeks | **ROI**: 184%

---

## What You're Building

Autom

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started: Cost Budget Enforcement (Issue #128)

**Your complete guide to implementing Issue #128**

**Priority**: P1-High | **Effort**: 1.5 weeks | **ROI**: 184%

---

## What You're Building

Automatic cost budget enforcement with throttling, alerts, and forecasting to prevent runaway costs.

**Why It Matters**: Misconfigured schedules can cause $500K+ cloud bill. Prevents financial disasters.

**Business Value**: $98K/year (risk mitigation + manual monitoring elimination + optimization)

---

## Before You Start (15 minutes)

### Understand Azure Cost Management API

**Resources**:
- [Azure Cost Management API](https://learn.microsoft.com/en-us/rest/api/cost-management/)
- Current implementation: `src/azure_haymaker/orchestrator/cost_query.py` (has 24-hour delay limitation)

### Key Challenge: Real-Time Cost Estimation

**Problem**: Azure Cost Management API has 24-hour delay
**Solution**: Estimate costs in real-time based on resource usage + Azure pricing API

---

## Phase 1: Budget Configuration (Days 1-2)

### Create Budget Config Model

**File**: `src/azure_haymaker/models/budget.py` (NEW)

```python
from pydantic import BaseModel
from typing import Literal

class BudgetConfig(BaseModel):
    """Budget configuration per schedule or tenant."""

    schedule_id: str
    tenant_id: str | None = None

    # Budget limits
    daily_limit_usd: float = 100.0
    weekly_limit_usd: float = 500.0
    monthly_limit_usd: float = 2000.0

    # Thresholds for alerts (percentage of limit)
    warning_threshold: float = 0.80  # 80%
    critical_threshold: float = 0.95  # 95%

    # Actions when threshold exceeded
    throttle_at_warning: bool = False
    throttle_at_critical: bool = True
    pause_at_limit: bool = True

class BudgetStatus(BaseModel):
    """Current budget utilization status."""

    period: Literal["daily", "weekly", "monthly"]
    limit_usd: float
    spent_usd: float
    remaining_usd: float
    utilization_percent: float
    forecast_end_of_perio

*[truncated — see source for full prompt]*