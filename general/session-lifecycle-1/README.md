# Session Lifecycle

> **Feature**: 014-session-lifecycle
**Status**: Complete

## Overview

The Session Lifecycle Management feature automatically saves and restores work c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Session Lifecycle Management

**Feature**: 014-session-lifecycle
**Status**: Complete

## Overview

The Session Lifecycle Management feature automatically saves and restores work context across CLI restarts, ensuring developers never lose track of what was completed or what's next.

**Key Benefits**:
- 🔄 **Automatic context restoration** - No manual re-orientation needed
- 📋 **Next actions queue** - Know exactly what to do next
- 📊 **Progress visibility** - See project progress at a glance
- ⚠️ **Blocker awareness** - Stay informed about issues requiring human input

## Core Concepts

### Session State File

- **Location**: `.codeframe/session_state.json` (per project)
- **Format**: JSON with human-readable formatting
- **Scope**: Per-project (each project has its own session state)
- **Persistence**: Saved on CLI exit (Ctrl+C or normal termination)
- **Restoration**: Loaded automatically on CLI start

### Session State Schema

```json
{
  "last_session": {
    "summary": "Completed Task #27 (JWT refresh tokens), Task #28 (Add token validation)",
    "completed_tasks": [27, 28],
    "timestamp": "2025-11-20T10:30:00"
  },
  "next_actions": [
    "Fix JWT validation in kong-gateway.ts (Task #29)",
    "Add refresh token tests (Task #30)",
    "Update auth documentation (Task #31)"
  ],
  "current_plan": "Implement OAuth 2.0 authentication with JWT tokens",
  "active_blockers": [
    {
      "id": 5,
      "question": "Which OAuth provider should we use for SSO?",
      "priority": "high"
    }
  ],
  "progress_pct": 68.5
}
```

## Usage Patterns

### 1. CLI Session Workflow

```bash
# Start or resume project (auto-restores session)
codeframe start my-app

# Output when session exists:
# 📋 Restoring session...
#
# Last Session:
#   Summary: Completed Task #27 (JWT refresh tokens)
#   Time: 2 hours ago
#
# Next Actions:
#   1. Fix JWT validation in kong-gateway.ts
#   2. Add refresh token tests
#   3. Update auth documentation
#
# Progress: 68% (27/40 tasks compl

*[truncated — see source for full prompt]*