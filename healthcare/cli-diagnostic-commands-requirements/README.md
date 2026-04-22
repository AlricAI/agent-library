# CLI DIAGNOSTIC COMMANDS REQUIREMENTS

> ## Executive Summary

This document specifies the implementation requirements for Phase 1 of CLI diagnostic commands for the Azure HayMaker orchestrat

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Diagnostic Commands for Azure Container Apps Orchestrator - Requirements Document

## Executive Summary

This document specifies the implementation requirements for Phase 1 of CLI diagnostic commands for the Azure HayMaker orchestrator. These commands enable operators to monitor, diagnose, and troubleshoot the Container Apps orchestrator instance through the `haymaker orch` command group.

**Requirement Type:** Feature
**Priority Level:** HIGH
**Complexity:** Medium (2-3 days)
**Estimated Effort:** 40-50 hours

---

## 1. Command Specifications

### 1.1 Command Hierarchy

All diagnostic commands are organized under the `orch` subcommand group:

```
haymaker orch <command> [options]
```

### 1.2 Command Definitions

#### 1.2.1 Status Command: `haymaker orch status`

**Purpose:** Display overall orchestrator status with endpoint information and active revisions

**Syntax:**
```bash
haymaker orch status [OPTIONS]
```

**Options:**
```
  --revision TEXT      Filter output to specific revision (optional)
  --format TEXT        Output format: table, json, yaml (default: table)
  --verbose, -v        Show additional details
  --help               Show this help message
```

**Output Fields (Table Format):**
| Field | Type | Description |
|-------|------|-------------|
| ENDPOINT | string | Container App endpoint URL |
| STATUS | string | Overall status (running, idle, degraded, error) |
| ACTIVE_REVISIONS | integer | Number of active revisions |
| CREATED | datetime | Container App creation date |

**Revisions Table (when multiple revisions):**
| Field | Type | Description |
|-------|------|-------------|
| NAME | string | Revision identifier |
| TRAFFIC | integer | Traffic percentage (0-100) |
| REPLICAS | integer | Number of replicas |
| HEALTH | string | Health status (healthy, unhealthy, unknown) |
| CREATED | datetime | Revision creation timestamp |

**Examples:**
```bash
# Show default orchestrator status
haymaker orch status

# Show as JSON
haymaker orch statu

*[truncated — see source for full prompt]*