# GETTING STARTED 125 VM SECURITY

> **Your complete guide to implementing Issue #125**

**Priority**: P0-Critical | **Effort**: 1-2 weeks | **ROI**: 1,165%

---

## What You're Fixing

C

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started: Windows VM Security Hardening (Issue #125)

**Your complete guide to implementing Issue #125**

**Priority**: P0-Critical | **Effort**: 1-2 weeks | **ROI**: 1,165%

---

## What You're Fixing

Critical security vulnerabilities in Windows VM provisioning (from PR #121):

1. 🔴 **Credentials exposed** in plaintext (logs)
2. 🔴 **Unrestricted NSG** rules (RDP from ANY IP)
3. 🟠 **Public IPs** on all VMs
4. 🟠 **No disk encryption**
5. 🟠 **No JIT access**

**Current Score**: 72/100 (C grade)
**Target Score**: 95+/100 (A grade)

---

## Before You Start (10 minutes)

### 1. Read the Spec
📄 **Full Specification**: [`specs/WINDOWS_VM_SECURITY_HARDENING.md`](../specs/WINDOWS_VM_SECURITY_HARDENING.md) (19KB)

**Key sections**:
- Security Assessment (vulnerabilities with CVSS scores)
- Threat Model (attack vectors)
- Implementation Plan (4 phases with code examples)

### 2. Review Current Code
```bash
# Read the INSECURE implementation
cat src/azure_haymaker/knowledge_worker/endpoints/windows_vm.py

# Review the security issues
# - Line ~200: Password returned in plaintext
# - Line ~150: NSG rule with source_address_prefix="*"
# - Line ~100: Public IP creation
# - Missing: Disk encryption configuration
# - Missing: JIT access policy
```

### 3. Review Starter Code
```bash
# See BEFORE and AFTER comparisons
cat examples/windows_vm_security_starter.py

# Note the SECURE implementation approach
```

---

## Phase 1: Key Vault Integration (Days 1-2, ~12 hours)

**Goal**: Store VM passwords in Azure Key Vault, not plaintext

### 1.1: Add Key Vault Client

**File**: `src/azure_haymaker/knowledge_worker/endpoints/windows_vm.py`

```python
from azure.keyvault.secrets import SecretClient

class WindowsVMManager:
    def __init__(self, ..., keyvault_name: str):
        # Add Key Vault client
        vault_url = f"https://{keyvault_name}.vault.azure.net"
        self.keyvault_client = SecretClient(vault_url, credential)
```

### 1.2: Modify provision_vm() Method

**

*[truncated — see source for full prompt]*