# UPGRADE

> Comprehensive guide for upgrading from older versions (v1–v3) to FINAL (v4).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Upgrading CloudCurio Monorepo

Comprehensive guide for upgrading from older versions (v1–v3) to FINAL (v4).

## Table of Contents

- [Overview](#overview)
- [Pre-Upgrade Checklist](#pre-upgrade-checklist)
- [Automated Upgrade](#automated-upgrade)
- [Manual Upgrade](#manual-upgrade)
- [Version-Specific Migration](#version-specific-migration)
- [Post-Upgrade Verification](#post-upgrade-verification)
- [Rollback Procedure](#rollback-procedure)
- [Breaking Changes](#breaking-changes)

## Overview

Manual merges between versions are error-prone and time-consuming. The CloudCurio upgrade script automates the process safely.

### What Changed in v4 (FINAL)

**Major Improvements:**
- ✅ **Repo Hardening**: CI/CD pipelines, pre-commit hooks, stronger validation
- ✅ **Agent Spec v1**: Formal schema with YAML→JSON compilation
- ✅ **Golden Eval Harness**: Automated test suite runner
- ✅ **Runtime Adapters**: Stable interfaces for local, langchain, pydanticai, crewai
- ✅ **Observability**: OpenTelemetry integration, health monitoring
- ✅ **Enhanced CLI**: New commands (cbw-doctor, cbw-index, cbw-capture)
- ✅ **Tool Ecosystem**: Expanded tool library with 45+ tools
- ✅ **Documentation**: Comprehensive KB, runbooks, ADRs

### Upgrade Safety

The upgrade process:
- ✅ **Creates automatic backups** before any changes
- ✅ **Preserves all custom content** (agents, workflows, configs)
- ✅ **Overlays framework files** without deleting your work
- ✅ **Validates** the upgrade with health checks
- ✅ **Supports rollback** if issues occur

## Pre-Upgrade Checklist

Before upgrading, complete these steps:

### 1. Verify Current Version

```bash
cd ~/Documents/cloudcurio_monorepo/cloudcurio-monorepo

# Check if pyproject.toml exists
cat pyproject.toml | grep version

# Or check git tags
git describe --tags
```

### 2. Commit All Changes

Ensure your working directory is clean:

```bash
git status

# If you have uncommitted changes
git add .
git commit -m "Pre-upgrade checkpoint"
```

### 3. Do

*[truncated — see source for full prompt]*