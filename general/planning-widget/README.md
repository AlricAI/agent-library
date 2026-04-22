# Planning Widget

> ## Context

The planning widget follows the stacked-card + timeline-rail layout and optimizes for long-running sessions (30-120 minutes).

The runtime

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Planning Widget

## Context

The planning widget follows the stacked-card + timeline-rail layout and optimizes for long-running sessions (30-120 minutes).

The runtime pane is designed around one principle:

- show where the active subagent is **inside its workflow** (`step number + step title`),
- not the orchestrator's internal QR fix-loop iteration counter.

## Design Goals

1. **Immediate progress readability**
   - The user should answer “how far along are we?” in one glance.
2. **Active worker clarity**
   - The widget should show who is running now and pool load (`queued/active/done`).
3. **Meaningful output accounting**
   - Show entity modifications as `+delta (total)`.
4. **Stable visual scan path**
   - Header + timeline + runtime + latest log remain in fixed positions.

## Runtime Information Hierarchy

From highest to lowest priority:

1. `step` (`current/total · title`)
2. step-based progress bar
3. active subagents block (role/model/load/mode)
4. modifications block (`Δ / total`)
5. latest log (auditable tail)

## Layout Overview

```
┌──────────────────────────────────── Runtime ──────────────────────────────────── 33m 14s ┐
│ step     : 2/6 · Codebase Exploration                                              │
│ progress : ███████░░░░░░░░░░ 33%                                                   │
│──────────────────────────────────────────┬──────────────────────────────────────────│
│ active subagents                         │ modifications (Δ / total)                │
│ role   : architect                       │ milestones : +2 (6)                      │
│ model  : anthropic/claude-opus-4-6       │ decisions  : +1 (9)                      │
│ load   : queued 0   active 1   done 0    │ intents    : +4 (18)                     │
│ mode   : single                          │ changes    : +0 (3)                      │
└──────────────────────────────────────────┴──────────────────────────────────────────┘
```

Elapsed time remains right-aligned in the to

*[truncated — see source for full prompt]*