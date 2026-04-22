# STA Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven STA flow for multi-corner, multi-mode timing closure. Covers constraint validation, 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Static Timing Analysis (STA) Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven STA flow for multi-corner, multi-mode timing closure. Covers constraint validation, timing analysis, exception handling, and timing sign-off for both pre-silicon and ECO cycles.

---

## 1. Shared State Object

```json
{
  "run_id": "sta_001",
  "design_name": "my_chip",
  "inputs": {
    "netlist":     "routed.v",
    "spef":        ["rc_best.spef", "rc_worst.spef"],
    "sdc":         "constraints.sdc",
    "libs":        { "ss": "ss_lib.lib", "ff": "ff_lib.lib", "tt": "tt_lib.lib" },
    "corners": [
      { "name": "setup_worst", "lib": "ss", "spef": "rc_worst", "voltage": 0.9, "temp": 125 },
      { "name": "hold_best",   "lib": "ff", "spef": "rc_best",  "voltage": 1.1, "temp": -40 },
      { "name": "typical",     "lib": "tt", "spef": "rc_worst", "voltage": 1.0, "temp": 25  }
    ]
  },
  "stages": {
    "constraint_validation": { "status": "pending", "output": {} },
    "multi_corner_analysis": { "status": "pending", "output": {} },
    "path_analysis":         { "status": "pending", "output": {} },
    "exception_review":      { "status": "pending", "output": {} },
    "eco_guidance":          { "status": "pending", "output": {} },
    "sta_signoff":           { "status": "pending", "output": {} }
  },
  "timing": {
    "setup_wns": null, "setup_tns": null,
    "hold_wns":  null, "hold_tns":  null,
    "failing_paths": []
  },
  "flow_status": "not_started"
}
```

---

## 2. Stage Sequence

```
[Constraint Validation] ──► [Multi-Corner Analysis] ──► [Path Analysis]
                                                              │ violations
                                                              ▼
                                                       [Exception Review]
                                                              │ invalid exceptions found
                                                              └──► back

*[truncated — see source for full prompt]*