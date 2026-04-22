# CLI DIAGNOSTIC FEATURES SPEC

> ## Executive Summary

During Container Apps orchestrator deployment and testing, numerous Azure CLI commands were required for diagnostics and trouble

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HayMaker CLI Diagnostic Features - Feature Specification

## Executive Summary

During Container Apps orchestrator deployment and testing, numerous Azure CLI commands were required for diagnostics and troubleshooting. This document proposes adding diagnostic capabilities to the HayMaker CLI to streamline orchestrator management and debugging.

## Problem Statement

Current workflow requires:
- Manual Azure CLI commands for status checking
- Multiple steps to diagnose container failures
- No unified interface for orchestrator health monitoring
- Difficult to track deployment state across revisions
- No easy way to view container logs or startup failures

## Diagnostic Commands Used

### 1. Orchestrator Status Check
**Azure CLI Commands:**
```bash
az containerapp show --name orch-dev-yc4hkcb2vv --resource-group haymaker-dev-rg \
  --query "properties.configuration.ingress.fqdn" -o tsv

az containerapp revision list --name orch-dev-yc4hkcb2vv --resource-group haymaker-dev-rg \
  --query "[?properties.active==\`true\`].{name:name, traffic:properties.trafficWeight, replicas:properties.replicas, health:properties.healthState}"
```

**What Info Needed:**
- Orchestrator endpoint URL
- Active revisions and traffic distribution
- Replica count and health status
- Whether orchestrator is scaled up or down

**Proposed CLI Command:**
```bash
haymaker orch status [--format json|table]
```

**Output:**
```
Orchestrator Status
===================
Endpoint: https://orch-dev-yc4hkcb2vv.ashyocean-9cc3722e.westus2.azurecontainerapps.io
Status: Running (scaled to 1 replica)

Active Revisions:
NAME                      TRAFFIC  REPLICAS  HEALTH    CREATED
orch-dev-yc4hkcb2vv--0002    0%       1      Healthy   2025-11-19T01:21:18Z
orch-dev-yc4hkcb2vv--0008   100%      0      None      2025-11-19T20:56:51Z
```

### 2. Replica Diagnostics
**Azure CLI Commands:**
```bash
az containerapp replica list --name orch-dev-yc4hkcb2vv --resource-group haymaker-dev-rg \
  --revision orch-dev-yc4hkcb

*[truncated — see source for full prompt]*