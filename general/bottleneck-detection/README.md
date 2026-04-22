# BOTTLENECK DETECTION

> ## Overview

The `LeadAgent.detect_bottlenecks()` method identifies workflow inefficiencies in real-time autonomous agent execution. It detects four p

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Workflow Bottleneck Detection

## Overview

The `LeadAgent.detect_bottlenecks()` method identifies workflow inefficiencies in real-time autonomous agent execution. It detects four primary bottleneck types with automatic severity classification and actionable recommendations.

## Configuration

The detection system uses configurable thresholds defined as class attributes on `LeadAgent`:

```python
DEPENDENCY_WAIT_THRESHOLD_MINUTES = 60       # Minutes before flagging blocked tasks
AGENT_OVERLOAD_THRESHOLD = 5                 # Tasks per agent threshold
CRITICAL_PATH_THRESHOLD = 3                  # Dependent tasks to flag as critical
CRITICAL_SEVERITY_WAIT_MINUTES = 120         # Minutes = critical severity
HIGH_SEVERITY_WAIT_MINUTES = 60              # Minutes = high severity
```

## Bottleneck Types

### 1. Dependency Wait

Detects tasks stuck on blocked dependencies.

**Triggers:**
- Task status = "blocked" OR task in blocked_tasks mapping
- Wait time >= 60 minutes (configurable)

**Severity Levels:**
- Critical: >= 120 minutes
- High: >= 60 minutes
- Medium: < 60 minutes

**Example Output:**
```python
{
    "type": "dependency_wait",
    "task_id": 42,
    "wait_time_minutes": 95,
    "blocking_task_id": 37,
    "severity": "high",
    "recommendation": "Task 42 has been waiting 95min on task 37. Investigate or manually unblock dependency."
}
```

### 2. Agent Overload

Detects agents with excessive task assignments.

**Triggers:**
- Agent status = "busy" AND workload > AGENT_OVERLOAD_THRESHOLD (default: 5)
- **Current Architecture**: Workload is binary (0 if idle, 1 if busy), so this bottleneck won't trigger in practice
- **Future-Ready**: Detection logic supports task queues when agents can handle multiple concurrent tasks

**Severity Levels:**
- High: workload > 8
- Medium: workload > 5
- Low: workload <= 5

**Example Output:**
```python
{
    "type": "agent_overload",
    "agent_id": "worker-1",
    "assigned_tasks": 6,  # In future queue-based architecture

*[truncated — see source for full prompt]*