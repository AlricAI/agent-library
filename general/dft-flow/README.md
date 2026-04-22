# DFT Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven DFT flow covering scan insertion, ATPG, BIST, JTAG/boundary scan, and DFT sign-off. 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Design for Test (DFT) Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven DFT flow covering scan insertion, ATPG, BIST, JTAG/boundary scan, and DFT sign-off. Ensures the manufactured chip is fully testable and meets quality targets (DPPM, fault coverage).

---

## 1. Shared State Object

```json
{
  "run_id": "dft_001",
  "design_name": "my_chip",
  "inputs": {
    "netlist":          "path/to/netlist.v",
    "sdc":              "constraints.sdc",
    "dft_spec":         "dft_architecture.md",
    "tech_lib":         "cells.lib",
    "fault_coverage_target": 99.0,
    "dppm_target":      10
  },
  "stages": {
    "dft_architecture":   { "status": "pending", "output": {} },
    "scan_insertion":     { "status": "pending", "output": {} },
    "atpg":               { "status": "pending", "output": {} },
    "bist_insertion":     { "status": "pending", "output": {} },
    "jtag_setup":         { "status": "pending", "output": {} },
    "dft_signoff":        { "status": "pending", "output": {} }
  },
  "fault_coverage": 0.0,
  "scan_chains":    [],
  "flow_status": "not_started"
}
```

---

## 2. Stage Sequence

```
[DFT Architecture] ──► [Scan Insertion] ──► [ATPG]
                              ▲                 │ coverage < target
                              └─────────────────┘
                                                │ coverage met
                         [BIST Insertion] ──► [JTAG Setup]
                                                │
                                         [DFT Sign-off]
                                                │ fail → Scan Insertion
                                                ▼ pass → Tape-out Ready
```

### Loop-Back Rules

| Failure                                   | Loop Back To    | Max |
|-------------------------------------------|-----------------|-----|
| Fault coverage < target after ATPG        | Scan Insertion  | 2   |
| Scan chain length imbalance > 20%         | 

*[truncated — see source for full prompt]*