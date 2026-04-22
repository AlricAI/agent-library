# CLI DIAGNOSTIC COMMANDS PROMPT

> ## Feature Request: CLI Diagnostic Commands for Orchestrator Management

### Objective

Implement Phase 1 of CLI diagnostic commands enabling operator

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Implementation Prompt: CLI Diagnostic Commands for Azure Container Apps Orchestrator

## Feature Request: CLI Diagnostic Commands for Orchestrator Management

### Objective

Implement Phase 1 of CLI diagnostic commands enabling operators to monitor, diagnose, and troubleshoot the Azure Container Apps orchestrator through the `haymaker orch` command group. This enables real-time visibility into orchestrator status, revision management, container logs, and health diagnostics without requiring direct Azure portal access.

### Requirements

**Functional Requirements:**

1. **Status Command** - `haymaker orch status`
   - Display orchestrator endpoint, overall status, active revision count
   - List active revisions with NAME, TRAFFIC, REPLICAS, HEALTH, CREATED columns
   - Support --revision filter for single revision details
   - Support table/json/yaml output formats
   - Handle multiple revisions, no revisions, and error states gracefully

2. **Replicas Command** - `haymaker orch replicas`
   - List replica status for specific revision
   - Show NAME, STATUS, CREATED, ERROR, CPU_USAGE, MEMORY_USAGE, RESTARTS
   - Support --status filtering (running/provisioning/failed)
   - Implement --follow mode with 2-second polling intervals
   - Require --revision when multiple active revisions exist
   - Support all output formats

3. **Logs Command** - `haymaker orch logs`
   - Retrieve container logs with options
   - Support --tail N (default 100, max 10000)
   - Implement --follow mode (stream new entries, Ctrl+C to stop)
   - Support --timestamps, --since DURATION, --container, --replica filters
   - Support text and json output formats
   - Handle no logs available edge case

4. **Health Command** - `haymaker orch health`
   - Basic checks: Container App status, DNS resolution, TCP connectivity, replica health
   - Deep checks (--deep): HTTP endpoint, API endpoints, Functions runtime, log errors
   - Generate pass/warn/fail status for each check
   - Provide actionable 

*[truncated — see source for full prompt]*