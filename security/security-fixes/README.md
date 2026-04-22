# SECURITY FIXES

> Detailed documentation of security vulnerabilities fixed in Azure HayMaker

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Fixes - PR #6
{: .no_toc }

This document summarizes all security fixes implemented in response to the security review of PR #6.
{: .fs-6 .fw-300 }

1. TOC
{:toc}

---

## Executive Summary

Fixed **8 security vulnerabilities** (3 CRITICAL, 5 HIGH severity) across the Azure HayMaker codebase:

- **CRITICAL**: SQL/OData injection, insecure file permissions, Key Vault network exposure
- **HIGH**: Race conditions, missing authentication, credential leaks, path traversal, error leaks

All fixes maintain Zero-BS philosophy with complete implementations and comprehensive test coverage.

---

## CRITICAL Severity Fixes

### CRITICAL-1: Table Storage SQL/OData Injection

**Issue**: User-controlled input directly interpolated into OData query filters without sanitization, allowing injection attacks.

**Files Fixed**:
- `src/azure_haymaker/orchestrator/execution_tracker.py`
- `src/azure_haymaker/orchestrator/rate_limiter.py`
- `src/azure_haymaker/orchestrator/agents_api.py`
- `src/azure_haymaker/orchestrator/sp_manager.py`
- `src/azure_haymaker/orchestrator/cleanup.py`

**Solution**:
- Added `sanitize_odata_value()` function that escapes single quotes by doubling them (OData standard)
- Applied sanitization to all user-controlled inputs used in filter queries
- Prevents injection attacks like: `exec' or PartitionKey ne ''`

**Example**:
```python
# Before (VULNERABLE):
query = f"PartitionKey eq '{execution_id}'"

# After (SECURE):
query = f"PartitionKey eq '{sanitize_odata_value(execution_id)}'"
```

**Test Coverage**: `tests/test_security.py::TestODataInjectionPrevention`

---

### CRITICAL-2: CLI Config File Permissions

**Issue**: Configuration files containing API keys created with default permissions (0644), making them world-readable on shared systems.

**Files Fixed**:
- `cli/src/haymaker_cli/config.py`

**Solution**:
- Set config directory permissions to 0700 (owner-only access)
- Set config file permissions to 0600 (owner read/write only)
- Apply permissio

*[truncated — see source for full prompt]*