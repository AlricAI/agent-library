# FPGA Emulation Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven flow for porting an ASIC design to an FPGA prototype platform. Enables pre-silicon h

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# FPGA Emulation & Prototyping Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven flow for porting an ASIC design to an FPGA prototype platform. Enables pre-silicon hardware/software co-development, performance validation, and early firmware bring-up — months before silicon is available.

---

## 1. Shared State Object

```json
{
  "run_id": "fpga_proto_001",
  "design_name": "my_soc",
  "inputs": {
    "rtl_filelist":      "filelist.f",
    "fpga_platform":     "Xilinx VCU118 | Intel Stratix 10 | Aldec HES",
    "fpga_part":         "xcvu9p-flga2104-2L-e",
    "target_freq":       "50MHz",
    "asic_target_freq":  "1GHz",
    "memory_map":        "path/to/memory_map.md",
    "debug_requirements":["JTAG", "ILA", "UART_console"]
  },
  "stages": {
    "rtl_adaptation":    { "status": "pending", "output": {} },
    "partitioning":      { "status": "pending", "output": {} },
    "fpga_synthesis":    { "status": "pending", "output": {} },
    "bring_up":          { "status": "pending", "output": {} },
    "sw_validation":     { "status": "pending", "output": {} },
    "proto_signoff":     { "status": "pending", "output": {} }
  },
  "fpga_utilization": {},
  "timing_met": false,
  "sw_tests_passing": 0,
  "flow_status": "not_started"
}
```

---

## 2. Stage Sequence

```
[RTL Adaptation] ──► [Partitioning] ──► [FPGA Synthesis]
                                              │ timing fail
                                              ▼ pass
                       [Bring-up] ──► [SW Validation]
                              ▲              │ HW/SW bug
                              └──────────────┘
                                             │ pass
                                      [Proto Sign-off]
```

---

## 3. Skill File Specifications

### 3.1 `sv-fpga-rtl-adapt/SKILL.md`

```markdown
# Skill: FPGA — RTL Adaptation

## Purpose
Modify ASIC RTL to be FPGA-compatible, replacing ASIC-specific
elements with FPGA equivalents.

*[truncated — see source for full prompt]*