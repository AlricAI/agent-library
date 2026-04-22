# PLANNING MODES

> ## Executive Summary

Tandem implements a **Plan-First** coding workflow designed for safety and clarity. The architecture ensures that AI-proposed ch

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Planning Modes Architecture

## Executive Summary

Tandem implements a **Plan-First** coding workflow designed for safety and clarity. The architecture ensures that AI-proposed changes are visually planned, strictly gated, and deterministic in execution.

**Core Principles:**

1.  **Visual Planning**: The AI writes a detailed Markdown plan to a file in `.opencode/plans/`.
2.  **Single Source of Truth**: The plan file is updated **in-place** (no clutter of `r001`, `r002` files).
3.  **Dynamic Tool Injection**: Planning capabilities are injected into OpenCode via `.opencode/agents/` on project load.
4.  **Strict Gating**: Execution is blocked until the user approves a specific hash of the (Markdown Content + Staged Operations).

---

## 1. Architecture Overview

### 1.1 State Machine

Tandem manages the planning lifecycle via a simplified state machine:

```
┌─────────┐    START      ┌──────────┐    PLAN_READY    ┌────────────┐
│  IDLE   │ ────────────▶ │ DRAFTING │ ───────────────▶ │ AWAITING_  │
│         │               │          │                  │ APPROVAL   │
└─────────┘               └──────────┘                  └────────────┘
     ▲                         ▲                              │
     │                         │                              │ REVISE
     │                         │ REQUEST_REVISION             │
     │                         │ (Update Plan File)           │
     │                         └──────────────────────────────┤
     │                                                        │
     │      ┌───────────┐     PLAN_EXECUTED     ┌───────────┐ │ BUILD (Hash Match)
     └──────│ COMPLETED │ ◀─────────────────────│ EXECUTING │◀┘
            │           │                       │           │
            └───────────┘                       └───────────┘
```

| State                 | Role                                | Input Gating                                    |
| --------------------- | -------------------------------

*[truncated — see source for full prompt]*