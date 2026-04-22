# Terminal App Research

> **Researcher:** researcher
**Team:** refactor-team
**Date:** 2026-02-22
**Status:** Complete

---

## Executive Summary

After extensive testing of Te

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Terminal.app Tab Management Research Report

**Researcher:** researcher
**Team:** refactor-team
**Date:** 2026-02-22
**Status:** Complete

---

## Executive Summary

After extensive testing of Terminal.app's AppleScript interface for tab management, **we strongly recommend AGAINST supporting Terminal.app tabs** in our project. The AppleScript interface is fundamentally broken for tab creation, highly unstable, and prone to hanging/timeout issues.

### Key Findings

| Capability | Status | Reliability |
|------------|--------|-------------|
| Create new tabs via AppleScript | ❌ **BROKEN** | Fails consistently |
| Create new windows via AppleScript | ✅ Works | Stable |
| Get tab properties | ⚠️ Partial | Unstable, prone to hangs |
| Set tab custom title | ✅ Works | Mostly stable |
| Switch between tabs | ❌ **NOT SUPPORTED** | N/A |
| Close specific tabs | ❌ **NOT SUPPORTED** | N/A |
| Get tab identifiers | ⚠️ Partial | Unstable |
| Overall stability | ❌ **POOR** | Prone to timeouts |

---

## Detailed Findings

### 1. Tab Creation Attempts

#### Method 1: `make new tab`
```applescript
tell application "Terminal"
    set newTab to make new tab at end of tabs of window 1
end tell
```
**Result:** ❌ **FAILS** with error:
```
Terminal got an error: AppleEvent handler failed. (-10000)
```

**Analysis:** The AppleScript dictionary for Terminal.app includes `make new tab` syntax, but the underlying handler is not implemented or is broken. This API exists but does not function.

#### Method 2: `do script in window`
```applescript
tell application "Terminal"
    do script "echo 'test'" in window 1
end tell
```
**Result:** ⚠️ **PARTIAL** - Executes command in existing tab, does NOT create new tab

**Analysis:** Despite documentation suggesting this might create tabs, it merely runs commands in the existing tab.

#### Method 3: `do script` without window specification
```applescript
tell application "Terminal"
    do script "echo 'test'"
end tell
```
**Result:** ✅ Creates new *

*[truncated — see source for full prompt]*