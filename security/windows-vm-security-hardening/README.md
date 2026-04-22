# WINDOWS VM SECURITY HARDENING

> **Status:** Critical | **Priority:** P0
**Security Score:** 72/100 (Current) → Target: 95+/100

---

## 1. Security Assessment

### Critical Vulnerabi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Windows VM Security Hardening Specification

**Status:** Critical | **Priority:** P0
**Security Score:** 72/100 (Current) → Target: 95+/100

---

## 1. Security Assessment

### Critical Vulnerabilities (Score Impact: -20 pts)

| Vulnerability | CVSS | Impact | Status |
|---|---|---|---|
| Credentials logged in plaintext | HIGH | Credential exposure in logs | CRITICAL |
| NSG allows RDP from ANY IP (*) | HIGH | Brute force, unauthorized access | CRITICAL |
| Public IPs on all VMs | MEDIUM | Network exposure surface | HIGH |
| No disk encryption | MEDIUM | Data at rest unprotected | HIGH |
| No JIT VM access | MEDIUM | Always-on attack surface | MEDIUM |
| Basic input validation | LOW | Injection vectors possible | MEDIUM |

### Current Threat Vectors

```
Attacker     RDP (ANY IP)     Public IP
   ↓             ↓                ↓
   └──────────────────────────────┘
                  ↓
            Admin password
              (plaintext in logs)
                  ↓
            VM compromised
                  ↓
        Data in plaintext OSes
```

---

## 2. Threat Model

### Attack Scenarios

**Scenario A: Log-Based Credential Theft**
- Admin password logged during provisioning
- Logs accessible via Azure Monitor, application logs, or file system
- Attacker gains permanent access to VM

**Scenario B: RDP Brute Force**
- NSG rule: `source_address_prefix: "*"` allows ANY IP
- Attacker performs dictionary attack on admin account
- No rate limiting, no JIT access delay

**Scenario C: Network Reconnaissance**
- Public IP directly accessible
- Attacker maps services on port 3389 (RDP)
- Escalates to internal network if compromised

---

## 3. Implementation Plan

### Phase 1: Credential Protection (Days 1-2) ⭐ START HERE

**Goal:** Remove passwords from plaintext logs, use Key Vault

**Key Changes:**

1. **Remove password from return value:**
   ```python
   # BEFORE: Returns plaintext password (INSECURE)
   result = {
       "admin_password": admin_password,  # Exposed!


*[truncated — see source for full prompt]*