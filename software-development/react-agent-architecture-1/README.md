# REACT AGENT ARCHITECTURE

> **Date**: 2026-02-07
**Status**: Draft
**Scope**: Replace Plan-and-Execute with ReAct loop for CodeFRAME's agent execution system

---

## 1. Architec

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ReAct Agent Architecture Plan

**Date**: 2026-02-07
**Status**: Draft
**Scope**: Replace Plan-and-Execute with ReAct loop for CodeFRAME's agent execution system

---

## 1. Architecture Overview

### What Changes

CodeFRAME's agent execution currently uses a **Plan-and-Execute** pattern:

```
PRD → Tasks → [Plan all steps upfront] → [Execute steps sequentially] → [Verify at end]
```

This is a known anti-pattern. Plans become stale as soon as step 1 produces unexpected output. The agent generates whole files without seeing what prior steps actually produced, leading to cross-file inconsistency, config overwrites, and ineffective self-correction.

The new architecture uses a **ReAct (Reason + Act) loop**:

```
PRD → Tasks → [Think: what should I do next?]
                       ↓
              [Act: call a tool (read, edit, create, search, run)]
                       ↓
              [Observe: what happened?]
                       ↓
              [Decide: task complete? keep going? stuck?]
                       ↓
              [Loop back to Think]
```

The LLM decides what to do at every step based on the current state of the codebase, not a predetermined plan. This is how Claude Code, SWE-agent, Warp, and every top SWE-bench performer works.

### What Stays the Same

| Module | Status | Notes |
|--------|--------|-------|
| `codeframe/core/workspace.py` | Unchanged | Workspace model is stable |
| `codeframe/core/tasks.py` | Unchanged | Task model is stable |
| `codeframe/core/gates.py` | Unchanged | Gate system works well |
| `codeframe/core/blockers.py` | Unchanged | Blocker system works well |
| `codeframe/core/events.py` | Unchanged | Event emission is stable |
| `codeframe/core/state_machine.py` | Unchanged | Status transitions are stable |
| `codeframe/core/runtime.py` | Minor change | Support new agent type via flag |
| `codeframe/core/context.py` | Minor change | Initial context loading still used, JIT retrieval added |
| `codeframe/core/streaming.py` | U

*[truncated — see source for full prompt]*