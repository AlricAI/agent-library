# HLS Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven HLS flow converting C/C++/SystemC algorithmic descriptions into RTL. Bridges the sof

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# High-Level Synthesis (HLS) Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven HLS flow converting C/C++/SystemC algorithmic descriptions into RTL. Bridges the software and hardware worlds. Covers algorithm analysis, HLS directives, RTL quality check, and co-simulation verification.

---

## 1. Architecture Overview

```
┌──────────────────────────────────────────────────────────────┐
│                    HLS ORCHESTRATOR                          │
│  Input:  C/C++ algorithm, performance/area targets, TB       │
│  Output: Verified RTL matching golden C model                │
└────────────────────────┬─────────────────────────────────────┘
                         │
     ┌───────────────────┼───────────────────────┐
     ▼                   ▼                       ▼
  Algorithm          HLS Synthesis          Co-simulation
  Analysis           Agent                  Agent
     │                   │                       │
  SKILL              SKILL                   SKILL
```

---

## 2. Shared State Object

```json
{
  "run_id": "hls_001",
  "design_name": "fft_block",
  "inputs": {
    "source_files":    ["fft.cpp", "fft.h"],
    "testbench":       "fft_tb.cpp",
    "golden_output":   "golden.dat",
    "target_freq":     "500MHz",
    "target_latency":  "256 cycles",
    "target_area":     "50K gates",
    "interface":       "AXI4-Stream",
    "tool":            "Vitis_HLS | Catapult | Stratus"
  },
  "stages": {
    "algorithm_analysis":  { "status": "pending", "output": {} },
    "directive_planning":  { "status": "pending", "output": {} },
    "hls_synthesis":       { "status": "pending", "output": {} },
    "rtl_qc":              { "status": "pending", "output": {} },
    "cosimulation":        { "status": "pending", "output": {} },
    "hls_signoff":         { "status": "pending", "output": {} }
  },
  "hls_report": {
    "latency_cycles": null,
    "ii":             null,
    "area_lut":       null,
    "area_f

*[truncated — see source for full prompt]*