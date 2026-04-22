# Hpc Routing Policy

> This document describes the on-chain scheduling enforcement for HPC job placement in VirtEngine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HPC Routing Policy and Fallback Rules

This document describes the on-chain scheduling enforcement for HPC job placement in VirtEngine.

## Overview

VE-5B implements routing enforcement to guarantee that jobs are placed according to x/hpc scheduling decisions. This ensures:

1. **Deterministic Routing**: Jobs are routed to clusters based on on-chain scheduling decisions
2. **Audit Trail**: All routing decisions and fallbacks are recorded for accountability
3. **Fail-Closed Behavior**: In strict mode, jobs cannot be placed without valid routing decisions
4. **Explicit Fallbacks**: When fallback routing is used, it is logged and auditable

## Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  Job Submission │───▶│ Routing Enforcer │───▶│  HPC Scheduler  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │
                              ▼
                     ┌──────────────────┐
                     │ x/hpc Scheduling │
                     │    Decision      │
                     └──────────────────┘
```

## Enforcement Modes

### Strict Mode (Default)

- Jobs **must** have a valid scheduling decision
- Jobs are rejected if the scheduled cluster is unavailable
- Cluster mismatch results in job rejection
- Stale decisions require re-scheduling

```yaml
routing:
  enforcement_mode: "strict"
  require_decision_for_submission: true
  allow_automatic_fallback: false
```

### Permissive Mode

- Jobs with missing decisions can proceed with new scheduling
- Automatic fallback to alternative clusters is allowed
- Stale decisions are automatically refreshed
- Violations are logged but jobs are not rejected

```yaml
routing:
  enforcement_mode: "permissive"
  require_decision_for_submission: false
  allow_automatic_fallback: true
```

### Audit-Only Mode

- No enforcement is applied
- All routing decisions and violations are logged
- Useful for monitoring before enabling enforcement

```yaml

*[truncated — see source for full prompt]*