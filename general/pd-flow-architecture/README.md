# PD Flow Architecture

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: This document defines the complete architecture for an AI-driven Physical Design (PD) flow. It

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Physical Design Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: This document defines the complete architecture for an AI-driven Physical Design (PD) flow. It is intended to be copied into a new session for implementation. It covers all skill file structures, stage agent designs, and the top-level orchestrator agent.

---

## 1. Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                   ORCHESTRATOR AGENT                        │
│  - Receives: Netlist, SDC, LEF/DEF, Technology files        │
│  - Manages: Stage sequencing, QoR state, loop-back logic    │
│  - Outputs: Final GDS, timing/power/area reports            │
└────────────────────┬────────────────────────────────────────┘
                     │ dispatches to
     ┌───────────────┼───────────────────────┐
     ▼               ▼                       ▼
┌─────────┐   ┌─────────────┐         ┌──────────────┐
│ Stage   │   │  Stage      │   ...   │  Stage       │
│ Agent 1 │   │  Agent 2    │         │  Agent N     │
│Floorplan│   │ Placement   │         │  Sign-off    │
└────┬────┘   └──────┬──────┘         └──────┬───────┘
     │               │                       │
     ▼               ▼                       ▼
┌─────────┐   ┌─────────────┐         ┌──────────────┐
│  SKILL  │   │   SKILL     │         │    SKILL     │
│floorplan│   │  placement  │         │   signoff    │
│.md      │   │  .md        │         │   .md        │
└─────────┘   └─────────────┘         └──────────────┘
```

### Core Principle
- **Skills** = domain knowledge per stage (rules, heuristics, SDC syntax, metrics)
- **Stage Agents** = execute one stage, evaluate QoR, return structured results
- **Orchestrator** = sequences stages, passes state, handles failures and loop-backs

---

## 2. Shared Data Contract (State Object)

All agents communicate through a single shared JSON state object. Every stage agent reads from and writes to this object

*[truncated — see source for full prompt]*