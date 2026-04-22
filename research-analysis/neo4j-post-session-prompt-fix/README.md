# NEO4J POST SESSION PROMPT FIX

> ## Problem

Neo4j was prompting users for database setup AFTER the session ended, creating a confusing user experience where questions appeared after 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Neo4j Post-Session Prompt Fix

## Problem

Neo4j was prompting users for database setup AFTER the session ended, creating a confusing user experience where questions appeared after Claude Code had already terminated the session.

## Root Cause

The issue occurred due to a **defense-in-depth gap** in the cleanup flow:

1. ✅ `stop.py` sets `AMPLIHACK_CLEANUP_MODE=1` environment variable (line 227)
2. ✅ `container_selection.resolve_container_name()` checks for this flag and returns default without prompting (lines 336-346) - **Primary Protection**
3. ❌ **Gap Found**: At line 360, when calling `unified_container_and_credential_dialog()`, it hardcoded `auto_mode=False`
4. ❌ **Vulnerability**: If neo4j config is initialized from anywhere other than through `resolve_container_name()`, prompts could still appear

### Code Flow Analysis

```
stop.py:_handle_neo4j_cleanup()
  ↓
os.environ["AMPLIHACK_CLEANUP_MODE"] = "1"  ✅ Sets flag
  ↓
Neo4jConnectionTracker.__init__()
  ↓
get_config()  # May reinitialize config
  ↓
config.py:Neo4jConfig.from_environment()
  ↓
container_selection.resolve_container_name()
  ↓
Lines 336-346: Check cleanup mode → return default ✅ Primary protection
  ↓ (if bypassed)
Line 360: unified_container_and_credential_dialog(auto_mode=False) ❌ Gap!
  ↓
unified_startup_dialog.py: Shows interactive prompts 😱
```

## Solution: Defense-in-Depth

Added **secondary protection layer** at the dialog invocation point (line 360):

### Implementation

**File**: `src/amplihack/memory/neo4j/container_selection.py`

**Before (Vulnerable)**:

```python
container_name = unified_container_and_credential_dialog(default_name, auto_mode=False)
```

**After (Defense-in-Depth)**:

```python
# Defense-in-depth: Check cleanup mode again as secondary protection
# (Primary check at lines 336-346, this prevents prompts if that check is bypassed)
# This ensures no interactive prompts during session cleanup regardless of code path
cleanup_mode_check = os.getenv("AMPLIHACK_CLEANUP

*[truncated — see source for full prompt]*