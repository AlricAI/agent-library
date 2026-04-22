# ENHANCEMENT DECISION TREE

> **Not sure which enhancement to work on?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhancement Selection Decision Tree

**Not sure which enhancement to work on? Follow this decision tree.**

---

## Start Here: What's Your Goal?

```
┌─────────────────────────────────────────────────────┐
│  What's your primary goal?                          │
└─────────────────────────────────────────────────────┘
                         │
         ┌───────────────┼───────────────┬──────────────────┐
         │               │               │                  │
         ▼               ▼               ▼                  ▼
    🔒 Security    💰 Revenue    ⚡ Operations    👨‍💻 Developer
         │               │               │            Experience
         │               │               │                  │
         ▼               ▼               ▼                  ▼
```

---

## 🔒 Security is My Priority

**If you want to fix critical security issues:**

```
Is production deployment blocked by security?
         │
    ┌────┴────┐
    │         │
   YES       NO
    │         │
    ▼         ▼
Issue #125  Consider
(VM Security) other goals
    │
    ▼
START HERE
(P0-Critical)
ROI: 1,165%
Effort: 1-2 weeks
```

**Action**: Start with Issue #125 (Windows VM Security Hardening)

**Why**:
- Blocks production deployment
- Highest ROI (1,165%)
- Lowest effort (1-2 weeks)
- Fixes 5 critical vulnerabilities

**Next steps**: Read [Getting Started: VM Security](GETTING_STARTED_125_VM_SECURITY.md)

---

## 💰 Revenue is My Priority

**If you want to generate new revenue streams:**

```
Do we already have customers ready for multi-tenant?
         │
    ┌────┴────┐
    │         │
   YES       NO
    │         │
    ▼         ▼
Issue #126  Issue #124
(Multi-Tenant) (SIEM Export)
    │         │
    ▼         ▼
Q2 2026    Q1 2026
ROI: 233%  ROI: 120%
$450K/yr   $150K/yr
```

**If YES**: **Issue #126 (Multi-Tenant Resource Isolation)**
- Opens SaaS market ($300K/year potential)
- Opens MSP market ($150K/year potential)
- ⚠️ Requires architecture review first
- Effort: 

*[truncated — see source for full prompt]*