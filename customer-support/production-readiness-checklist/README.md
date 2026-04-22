# PRODUCTION READINESS CHECKLIST

> **Purpose**: Verify Azure HayMaker is production-ready before deploying to customer environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Production Readiness Checklist

**Purpose**: Verify Azure HayMaker is production-ready before deploying to customer environments.

**Last Updated**: 2025-11-30

---

## ⚠️ CURRENT STATUS: NOT PRODUCTION READY

**Blockers**:
- 🔴 **Issue #125**: Windows VM Security Hardening (P0-Critical)
- 🔴 **Issue #124**: SIEM Telemetry Export (P0-Critical for red team use case)

**Merge PR #119 first** to unblock Issue #124.

---

## Security Checklist

### Critical Security Requirements

- [ ] **Credentials in Key Vault** - No plaintext passwords in code/logs
  - 🔴 **BLOCKED**: Issue #125 (Windows VM credentials exposed)
  - Files: `src/azure_haymaker/knowledge_worker/endpoints/windows_vm.py`

- [ ] **Network Security** - Restricted NSG rules, no public IPs
  - 🔴 **BLOCKED**: Issue #125 (RDP from ANY IP, public IPs on all VMs)
  - Files: `src/azure_haymaker/knowledge_worker/endpoints/windows_vm.py`

- [ ] **Disk Encryption** - Azure Disk Encryption enabled
  - 🔴 **BLOCKED**: Issue #125 (VMs not encrypted)

- [ ] **JIT Access** - Just-In-Time VM access configured
  - 🔴 **BLOCKED**: Issue #125 (No JIT policies)

- [ ] **SIEM Integration** - Telemetry exported to customer SIEM
  - 🔴 **BLOCKED**: Issue #124 (No SIEM export capability)
  - **Impact**: Core use case not functional

- [ ] **Security Scanning** - No hardcoded secrets detected
  - ✅ **PASS**: pre-commit hooks check for secrets

- [ ] **Azure AD Authentication** - Orchestrator API requires auth
  - ✅ **PASS**: `src/azure_haymaker/orchestrator/auth.py` implemented

---

## Infrastructure Checklist

### Required Services

- [ ] **Azure Container Apps** - Agent execution environment
  - ✅ Configured in `infra/bicep/`
  - ⚠️ Verify capacity limits for target scale

- [ ] **Azure App Service** - Orchestrator hosting
  - ✅ Deployed at `haymaker-fastapi-app.azurewebsites.net`
  - ⚠️ Verify SKU supports expected load

- [ ] **Azure Key Vault** - Secrets management
  - ⚠️ **REQUIRED**: Issue #125 (not yet integrated for VM

*[truncated — see source for full prompt]*