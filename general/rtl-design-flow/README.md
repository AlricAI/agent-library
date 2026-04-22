# RTL Design Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven RTL design flow in SystemVerilog. Covers module planning, RTL coding, linting, CDC/R

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RTL Design Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven RTL design flow in SystemVerilog. Covers module planning, RTL coding, linting, CDC/RDC analysis, and synthesis readiness sign-off. Takes the microarchitecture document as input and produces a synthesis-ready RTL package.

---

## 1. Architecture Overview

```
┌──────────────────────────────────────────────────────────────┐
│                    RTL DESIGN ORCHESTRATOR                   │
│  Input:  Microarch doc, interface specs, coding guidelines    │
│  Output: Lint-clean, CDC-clean, synthesis-ready RTL          │
└────────────────────────┬─────────────────────────────────────┘
                         │
     ┌───────────────────┼───────────────────────┐
     ▼                   ▼                       ▼
┌──────────┐     ┌──────────────┐       ┌───────────────┐
│  Stage   │     │   Stage      │       │   Stage       │
│  Agent   │     │   Agent      │  ...  │   Agent       │
│  Module  │     │  RTL Coding  │       │  Synth Ready  │
│  Planning│     │  & Review    │       │  Sign-off     │
└────┬─────┘     └──────┬───────┘       └───────┬───────┘
     │                  │                       │
     ▼                  ▼                       ▼
  SKILL               SKILL                   SKILL
```

---

## 2. Shared State Object

```json
{
  "run_id": "rtl_design_001",
  "design_name": "my_block",
  "inputs": {
    "microarch_doc":   "path/to/microarch.md",
    "interface_spec":  "path/to/interfaces.md",
    "coding_guidelines": "path/to/guidelines.md",
    "technology":      "tsmc7nm",
    "target_frequency": "1GHz"
  },
  "stages": {
    "module_planning":   { "status": "pending", "output": {} },
    "rtl_coding":        { "status": "pending", "output": {} },
    "lint_check":        { "status": "pending", "output": {} },
    "cdc_rdc_analysis":  { "status": "pending", "output": {} },
    "synth_check":       { "status": "pending", "output": {} },
    "

*[truncated — see source for full prompt]*