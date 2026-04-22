# Intake Dashboard Ux

> > **Scope:** Browser-based UX for the intake phase only (context analysis → scout exploration → elicitation → consolidation).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Intake Dashboard UX Flow — Complete Design

> **Scope:** Browser-based UX for the intake phase only (context analysis → scout exploration → elicitation → consolidation).
> **Data sources:** Projection (`state.json`), event log (`events.jsonl`), IPC files (`ipc.json`), scout subagent directories.

---

## State Machine Overview

The browser moves through 6 states during intake. Each state has a distinct visual identity but shares a persistent layout frame.

```
┌──────────┐    SSE connect     ┌───────────────┐   step_transition(1)  ┌──────────────────┐
│ Loading  │ ──────────────────→│    Context     │ ────────────────────→ │      Scout       │
│ (shell)  │                    │   Analysis     │                       │   Exploration    │
└──────────┘                    └───────────────┘                       └──────────────────┘
                                                                              │
                                                                    step_transition(3) +
                                                                    ipc ask request
                                                                              │
┌──────────────┐  all questions   ┌───────────────┐   ask SSE event   ┌──────────────────┐
│Consolidation │←─── answered ────│  Elicitation   │←─────────────────│  Scout → Elicit  │
│              │                  │  (questions)   │                   │   (transition)   │
└──────────────┘                  └───────────────┘                   └──────────────────┘
```

The transition from Scout Exploration to Elicitation is actually seamless — step 3 starts (Gap Analysis & Questions), the intake model reads scout findings, and then asks questions. The browser detects the `ask` SSE event as the moment to shift from progress-watching to interactive mode.

---

## Persistent Layout Frame

Every state renders inside the same page structure. This prevents disorienting full-page transitions.

```
┌─────────────────────────

*[truncated — see source for full prompt]*