# GETTING STARTED 132 DASHBOARD

> **Your complete guide to implementing Issue #132**

**Priority**: P2-Medium | **Effort**: 3 weeks | **ROI**: 160%

---

## What You're Building

Build

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started: Real-Time Analytics Dashboard (Issue #132)

**Your complete guide to implementing Issue #132**

**Priority**: P2-Medium | **Effort**: 3 weeks | **ROI**: 160%

---

## What You're Building

Build a real-time analytics dashboard showing agent execution, costs, telemetry volume, and system health with WebSocket updates and interactive filtering.

**Why It Matters**: Operational visibility. You can't manage what you can't see. Demo-friendly UI for stakeholders.

**Business Value**: Faster issue detection, better resource understanding, improves stakeholder confidence.

---

## Before You Start (20 minutes)

### 1. Understand Current Metrics

```bash
# See what telemetry is currently collected
find src -name "*telemetry*" -o -name "*metrics*" | head -10
grep -r "class.*Metric\|async def.*metric" src/ | head -5
```

### 2. Understand Architecture Needs

- **Backend**: FastAPI with WebSocket support
- **Frontend**: React with real-time chart updates
- **Data source**: Existing telemetry from PR #119
- **Hosting**: Azure Static Web Apps + API backend

### 3. Check Dependencies

```bash
# Check if websockets is available
grep -i "websockets\|fastapi" pyproject.toml
```

---

## Phase 1: Implement Backend WebSocket Endpoint (Days 1-3, ~12 hours)

### Create Branch

```bash
git checkout main
git pull origin main
git checkout -b feat/issue-132-analytics-dashboard
```

### Create Backend Structure

```bash
mkdir -p src/azure_haymaker/orchestrator/metrics
mkdir -p src/azure_haymaker/orchestrator/websocket
touch src/azure_haymaker/orchestrator/metrics/__init__.py
touch src/azure_haymaker/orchestrator/metrics/aggregator.py
touch src/azure_haymaker/orchestrator/websocket/__init__.py
touch src/azure_haymaker/orchestrator/websocket/manager.py
```

### Implement Metrics Aggregator

**File**: `src/azure_haymaker/orchestrator/metrics/aggregator.py`

```python
from datetime import datetime, timedelta
from typing import Dict, List
import asyncio

class MetricsAggregator:

*[truncated — see source for full prompt]*