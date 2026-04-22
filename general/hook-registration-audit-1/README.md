# HOOK REGISTRATION AUDIT

> ## Purpose

Verify ALL amplihack hooks are registered in `hooks.json` with `${CLAUDE_PLUGIN_ROOT}` variable paths.

## Problem

Issue #1948 requiremen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Hook Registration Audit

## Purpose

Verify ALL amplihack hooks are registered in `hooks.json` with `${CLAUDE_PLUGIN_ROOT}` variable paths.

## Problem

Issue #1948 requirement #2: "ALL hooks with ${CLAUDE_PLUGIN_ROOT}". Currently:

- `hooks.json` has 4 hooks registered (SessionStart, Stop, PostToolUse, PreCompact)
- Directory `~/.amplihack/.claude/tools/amplihack/hooks/` contains 7 Python hook files
- 3 hooks may be missing from `hooks.json`: `pre_tool_use.py`, `user_prompt_submit.py`, `power_steering_checker.py`

## Solution Overview

1. Audit `~/.amplihack/.claude/tools/amplihack/hooks/` directory for all hook files
2. Compare against `hooks.json` entries
3. Add missing hooks to `hooks.json` with proper configuration
4. Verify all paths use `${CLAUDE_PLUGIN_ROOT}` variable

## Contract

### Inputs

**Directory Audit:**

- Scan `~/.amplihack/.claude/tools/amplihack/hooks/*.py` for hook files
- Exclude test files (`test_*.py`) and `__init__.py`

**Current `hooks.json`:**

```json
{
  "SessionStart": [...],
  "Stop": [...],
  "PostToolUse": [...],
  "PreCompact": [...]
}
```

### Outputs

**Updated `hooks.json`:**

```json
{
  "SessionStart": [...],
  "Stop": [...],
  "PreToolUse": [...],        // ADDED
  "PostToolUse": [...],
  "UserPromptSubmit": [...],  // ADDED
  "PreCompact": [...]
}
```

### Side Effects

- Updates `~/.amplihack/.claude/tools/amplihack/hooks/hooks.json` with complete hook list
- Ensures all hooks load properly in Claude Code

## Implementation Design

### Step 1: Audit Hook Files

**Command:**

```bash
ls .claude/tools/amplihack/hooks/*.py | grep -v test_ | grep -v __init__
```

**Expected Files (from git status):**

```
.claude/tools/amplihack/hooks/
├── session_start.py          ✅ In hooks.json (SessionStart)
├── stop.py                   ✅ In hooks.json (Stop)
├── post_tool_use.py          ✅ In hooks.json (PostToolUse)
├── pre_compact.py            ✅ In hooks.json (PreCompact)
├── pre_tool_use.py           ❌ MISSING

*[truncated — see source for full prompt]*