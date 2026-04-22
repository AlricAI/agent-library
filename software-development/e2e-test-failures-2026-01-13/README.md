# E2e Test Failures 2026 01 13

> ## Summary

| Category | Count |
|----------|-------|
| Failed | 39 |
| Flaky | 13 |
| Skipped | 25 |
| Did not run | 19 |
| Passed | 559 |
| **Total*

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# E2E Test Failures Report - 2026-01-13

## Summary

| Category | Count |
|----------|-------|
| Failed | 39 |
| Flaky | 13 |
| Skipped | 25 |
| Did not run | 19 |
| Passed | 559 |
| **Total** | **655** |
| **Duration** | 46.6m |

---

## Critical Issues (Grouped by Root Cause)

### Issue #1: Mobile Viewport Detection Bug

**Severity:** High
**Affected Browsers:** Mobile Chrome, Mobile Safari
**Affected Tests:** 3

The test incorrectly detects mobile browsers as desktop, then asserts desktop viewport width >800 when the actual mobile width is ~390px.

**Failing Tests:**
- `[Mobile Chrome] › test_mobile_smoke.spec.ts:50:7 › should have correct mobile viewport @smoke`
- `[Mobile Safari] › test_mobile_smoke.spec.ts:50:7 › should have correct mobile viewport @smoke`

**Error:**
```
Error: expect(received).toBeGreaterThan(expected)
Expected: > 800
Received:   393  (or 390 for Safari)
```

**Root Cause Analysis:**
The test runs `mobile: false` detection when it should detect `mobile: true` for Mobile Chrome/Safari projects:
```
Running mobile test on: chromium (mobile: false)
ℹ️ Desktop viewport: 1280x720 (not a mobile test)
```

**Location:** `tests/e2e/test_mobile_smoke.spec.ts:50-64`

**Fix:** Update mobile detection logic in playwright config or test setup to correctly identify Mobile Chrome/Safari projects.

---

### Issue #2: Project Phase State Mismatch (Seed Data)

**Severity:** High
**Affected Browsers:** Firefox, WebKit, Mobile Chrome, Mobile Safari
**Affected Tests:** 10+

Tests expect project to be in `planning` phase but receive `active` phase instead.

**Failing Tests:**
- `test_late_joining_user.spec.ts:129` - should show "Tasks Ready" section @smoke
- `test_state_reconciliation.spec.ts:132` - should show "Review Tasks" @smoke
- `test_state_reconciliation.spec.ts:657` - should maintain correct state after page refresh @smoke

**Error:**
```
Error: expect(received).toBe(expected) // Object.is equality
Expected: "planning"
Received: "active"
```

**Root Cause

*[truncated — see source for full prompt]*