# Timeout Investigation Findings

> **Date:** 2025-01-09  
**Issue:** Commands sometimes behave strangely with timeouts - "weird stuff happened"

---

## 🔍 **What We Discovered**

### *

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RunShellCommand Timeout Investigation - Findings & Fix

**Date:** 2025-01-09  
**Issue:** Commands sometimes behave strangely with timeouts - "weird stuff happened"

---

## 🔍 **What We Discovered**

### **Two Timeout Mechanisms Racing**

`PersistentShellProcess.WaitForMarkerAsync()` has **TWO different timeout mechanisms**:

1. **CancellationToken mechanism** (Modern, correct)
   - Created in `RunCommandAsync` line 139: `new CancellationTokenSource(timeout)`
   - Passed to `Task.Delay(50, cancellationToken)` 
   - Throws `OperationCanceledException` when timeout fires
   - Shell stays alive, gets promoted correctly ✅

2. **Manual timeout check** (Old, problematic)
   - Lines 511-533 in `WaitForMarkerAsync`
   - Checks `if (elapsed > actualTimeoutMs)`
   - Throws `TimeoutException`
   - Caught in `RunCommandInternalAsync` line 268
   - Calls `ForceShutdown()` - **KILLS THE SHELL** ❌
   - Shell promotion fails

---

## 🎯 **The Race Condition**

**Normal case (works fine):**
```
Loop iteration:
1. Read output (5ms)
2. Check regex (1ms)
3. Manual timeout check (passes, we're at 1950ms < 2000ms)
4. Task.Delay(50, cancellationToken) starts
5. CancellationToken fires at 2000ms
6. Task.Delay throws OperationCanceledException ✅
7. Shell stays alive, gets promoted
```

**Bad case (causes problems):**
```
Loop iteration at T=1950ms:
1. Read output (slow due to lock contention - 30ms)
2. Check regex (slow on large output - 40ms)
3. Now at T=2020ms
4. Manual timeout check: 2020ms > 2000ms ❌
5. Throws TimeoutException
6. Never reaches Task.Delay
7. Caught in RunCommandInternalAsync
8. Calls ForceShutdown() - KILLS SHELL ❌
9. RunShellCommand tries to promote dead shell
10. Weird stuff happens!
```

---

## 📊 **Evidence**

We **proved this happens** by adding deliberate delays (lines 513-523) to slow down the loop:

```
Line 988: 🐌 DELIBERATELY SLOWING DOWN - elapsed=1915ms, adding 134ms delay
Line 989: 🐌 Woke from deliberate delay - elapsed=2059ms  
Line 990: ⏱️ Timeout ch

*[truncated — see source for full prompt]*