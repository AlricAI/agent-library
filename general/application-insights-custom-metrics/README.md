# APPLICATION INSIGHTS CUSTOM METRICS

> ## Overview

Azure HayMaker emits custom metrics to Azure Application Insights for operational visibility and monitoring. These metrics track orchestr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Application Insights Custom Metrics

## Overview

Azure HayMaker emits custom metrics to Azure Application Insights for operational visibility and monitoring. These metrics track orchestrator execution performance, scenario activity, cleanup operations, and resource management.

## Available Metrics

### 1. Execution Duration (`haymaker.execution.duration_seconds`)

**Type:** Histogram (float)
**Unit:** Seconds
**Description:** Total duration of orchestrator execution from timer trigger start to completion.

**Dimensions:**
- `run_id`: Unique identifier for the orchestration run
- `status`: Execution status (`success`, `failure`, `timeout`)

**Example Query (KQL):**
```kusto
customMetrics
| where name == "haymaker.execution.duration_seconds"
| summarize avg(value), percentile(value, 95), percentile(value, 99) by bin(timestamp, 1h)
```

### 2. Scenarios Executed (`haymaker.scenarios.executed_count`)

**Type:** Counter (int)
**Unit:** Count
**Description:** Number of automation scenarios executed in each orchestration run.

**Dimensions:**
- `run_id`: Unique identifier for the orchestration run
- `scenario_type`: Type of scenario executed

**Example Query (KQL):**
```kusto
customMetrics
| where name == "haymaker.scenarios.executed_count"
| summarize sum(value) by bin(timestamp, 1h), scenario_type
```

### 3. Cleanup Success (`haymaker.cleanup.success`)

**Type:** Gauge (0 or 1)
**Unit:** Boolean (0=failure, 1=success)
**Description:** Indicates whether resource cleanup completed successfully after scenario execution.

**Dimensions:**
- `run_id`: Unique identifier for the orchestration run
- `cleanup_phase`: Phase of cleanup (`resources`, `storage`, `network`)

**Example Query (KQL):**
```kusto
customMetrics
| where name == "haymaker.cleanup.success"
| summarize success_rate = avg(value) by bin(timestamp, 1h)
```

### 4. Resources Created (`haymaker.resources.created_count`)

**Type:** Counter (int)
**Unit:** Count
**Description:** Number of Azure resources created d

*[truncated — see source for full prompt]*