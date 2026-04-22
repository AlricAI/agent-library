# CLAUDE

> ## 🚨 CRITICAL: WebtoysOS v3 Authentication System 🚨

**IMPORTANT**: When creating apps that need user authentication, see `AUTH-DOCUMENTATION.md` fo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Issue Tracker - Critical Rules for Claude Code

## 🚨 CRITICAL: WebtoysOS v3 Authentication System 🚨

**IMPORTANT**: When creating apps that need user authentication, see `AUTH-DOCUMENTATION.md` for complete details on how the desktop broadcasts auth to apps via postMessage.

Quick summary:
- Desktop handles all login/logout
- Apps receive auth via `TOYBOX_AUTH` postMessage
- User object contains `handle` and `participantId`
- Apps should NEVER create their own login forms

## 🚨 CRITICAL: CRON COMPATIBILITY FIXES 🚨

**STOP! READ THIS FIRST BEFORE MAKING ANY CHANGES!**

The agent-issue-tracker has specific requirements for cron compatibility that MUST be preserved:

### ⚠️ NEVER REMOVE THESE CRITICAL LINES ⚠️

1. **In monitor.js** - MUST have at the start of the `monitor()` function:
```javascript
// CRITICAL: Change to script directory - MUST be first line for cron compatibility
process.chdir(__dirname);
```

2. **In reformulate-issues.js and fix-issues.js** - MUST use full path to claude:
```javascript
// Use full path: /Users/bartdecrem/.local/bin/claude
// NOT just: claude
```

### 🔴 WHY THIS KEEPS BREAKING 🔴

**The auto-fix agent switches git branches**, which can discard uncommitted changes to these files! 
- When fix-issues.js runs `git checkout` to create branches, it loses uncommitted changes
- This causes the fixes to disappear every 2 minutes when cron runs
- **ALWAYS COMMIT THESE CRITICAL FIXES** before the cron runs again

### ✅ HOW TO FIX IF BROKEN AGAIN

```bash
# 1. Add process.chdir(__dirname) to monitor.js
# 2. Use full claude path in reformulate-issues.js and fix-issues.js  
# 3. IMMEDIATELY COMMIT:
git add monitor.js reformulate-issues.js fix-issues.js CLAUDE.md
git commit -m "fix: Restore critical cron compatibility fixes"
git push origin main  # Push to main so agent machine gets the fixes
```

## 🛑 CRITICAL: Branch Switching and Data Loss Prevention

### The Problem
The auto-fix agent (`fix-issues.js`) creates new Git branches for

*[truncated — see source for full prompt]*