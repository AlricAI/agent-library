# Discovery Flow Analysis

> **Last Updated**: 2026-01-04

## Implementation Status

| Issue | Priority | Status | Description |
|-------|----------|--------|-------------|
| Issu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Discovery Flow Analysis

**Last Updated**: 2026-01-04

## Implementation Status

| Issue | Priority | Status | Description |
|-------|----------|--------|-------------|
| Issue 1 | P0 | ✅ FIXED | Race condition - Added `discovery_question_ready` WebSocket broadcast |
| Issue 3 | P0 | ✅ FIXED | Stuck discovery - Fixed fallback in `start_discovery()`, added timeout detection, fixed `_save_discovery_state()` to persist question text |
| Issue 4 | P1 | ✅ FIXED | PRD retry - Added `POST /api/projects/{id}/discovery/generate-prd` endpoint |
| Issue 6 | P1 | ✅ FIXED | Error recovery UI - Added Restart Discovery and Retry PRD buttons |
| Issue 8 | P3 | ✅ FIXED | WebSocket gaps - Added `discovery_question_ready`, `discovery_reset` |
| Issue 2 | P2 | ⏳ PENDING | WebSocket handlers for answer flow |
| Issue 5 | P2 | ⏳ PENDING | View PRD button state awareness |
| Issue 7 | P2 | ⏳ PENDING | Orphan state detection |

## Complete State Machine

```
PROJECT STATES:
  init → running → paused → completed
         ↓
  (phase: discovery → planning → development → review → completed)

DISCOVERY STATES:
  idle → discovering → completed

PRD STATES:
  not_started → generating → completed | failed
```

## Current Flow Issues

### Issue 1: Race Condition in Project Start
**Location**: `ProjectList.tsx:handleProjectCreated()` + `agents.py:start_project_agent()`

**Problem**: After project creation, the frontend navigates to `/projects/{id}` immediately after calling `startProject()`. The navigation can complete before the background task sets up discovery, causing the DiscoveryProgress component to poll and find discovery in "idle" state but with no "Start Discovery" button visible (the state becomes ambiguous).

**Symptoms**:
- Shows "0/0 0%" with no question
- "Preparing discovery questions..." spinner shows but question never appears
- Discovery state is "discovering" but `current_question_id` is None

**Fix**:
1. The `start_agent()` function should be atomic - it should complete disco

*[truncated — see source for full prompt]*