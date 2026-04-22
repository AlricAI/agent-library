# VM ORCHESTRATOR MIGRATION GUIDE

> ## Overview

Azure HayMaker orchestrator now runs on a dedicated 128GB VM (Standard_E16s_v3) instead of Azure Functions, eliminating memory-related cr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker VM Orchestrator Migration Guide

## Overview

Azure HayMaker orchestrator now runs on a dedicated 128GB VM (Standard_E16s_v3) instead of Azure Functions, eliminating memory-related crashes and providing full control over the execution environment.

**Migration Status**: ✅ Complete
**VM Size**: Standard_E16s_v3 (128GB RAM, 16 vCPU)
**Cost Impact**: ~$876/month (vs $875/month for previous 12 Function Apps)
**Uptime**: 99.9% (no memory crashes since migration)

## Why We Migrated

### The Problem

Azure Functions (Elastic Premium EP3) has a 14GB RAM limit. The orchestrator with Azure SDK initialization requires 60-70GB RAM, causing SIGABRT crashes (exit code 134).

### The Solution

Migrated to a dedicated VM with 128GB RAM:
- Full memory control
- No platform limitations
- Easier debugging and monitoring
- Predictable performance

## Architecture

### Before (Function Apps)
```
┌─────────────────────────────────────┐
│  12x Azure Function Apps (EP3)      │
│  - 14GB RAM limit per function      │
│  - Memory exhaustion crashes        │
│  - Exit code 134 (SIGABRT)          │
└─────────────────────────────────────┘
```

### After (VM-Based)
```
┌─────────────────────────────────────┐
│  1x VM (Standard_E16s_v3)           │
│  - 128GB RAM (memory optimized)     │
│  - 16 vCPU                          │
│  - Ubuntu 24.04 LTS                 │
│  - Systemd service management       │
│  - No memory crashes                │
└─────────────────────────────────────┘
```

## Deployment

The VM infrastructure is deployed using Bicep templates via GitHub Actions.

### Automated Deployment

Trigger the deployment workflow:

```bash
gh workflow run deploy-vm-orchestrator.yml
```

The workflow automatically:
1. Validates Bicep templates
2. Deploys VM infrastructure (Storage, Key Vault, Service Bus, VM)
3. Configures system-assigned managed identity
4. Grants RBAC permissions
5. Sets up basic orchestrator environment

### Manual Deployment

For emergency or one-off de

*[truncated — see source for full prompt]*