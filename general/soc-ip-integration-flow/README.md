# SoC IP Integration Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven flow for assembling a complete SoC from first-party RTL blocks, licensed hard/soft I

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SoC IP Integration Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven flow for assembling a complete SoC from first-party RTL blocks, licensed hard/soft IPs, and memory macros. Covers IP procurement, integration, bus fabric configuration, and chip-level verification.

---

## 1. Shared State Object

```json
{
  "run_id": "soc_integration_001",
  "soc_name": "my_soc",
  "inputs": {
    "arch_doc":        "path/to/microarch.md",
    "ip_list": [
      { "name": "ARM_Cortex_M33", "type": "hard_ip", "vendor": "ARM" },
      { "name": "USB3_PHY",       "type": "hard_ip", "vendor": "Synopsys" },
      { "name": "AXI_Interconnect","type": "soft_ip","vendor": "internal" },
      { "name": "SRAM_256K",      "type": "memory_macro", "vendor": "foundry" }
    ],
    "bus_fabric":      "AXI4 + APB3",
    "technology":      "tsmc7nm"
  },
  "stages": {
    "ip_procurement":     { "status": "pending", "output": {} },
    "ip_configuration":   { "status": "pending", "output": {} },
    "bus_fabric_setup":   { "status": "pending", "output": {} },
    "top_integration":    { "status": "pending", "output": {} },
    "chip_level_sim":     { "status": "pending", "output": {} },
    "integration_signoff":{ "status": "pending", "output": {} }
  },
  "ip_status": {},
  "connectivity_errors": [],
  "flow_status": "not_started"
}
```

---

## 2. Stage Sequence

```
[IP Procurement] ──► [IP Configuration] ──► [Bus Fabric Setup]
                                                    │
                              ▼
                       [Top Integration] ──► [Chip-Level Sim]
                              ▲                     │ connectivity errors
                              └─────────────────────┘
                                                    │ pass
                              [Integration Sign-off]
```

---

## 3. Skill File Specifications

### 3.1 `sv-soc-ip-procurement/SKILL.md`

```markdown
# Skill: SoC — IP Procurement and Quality

*[truncated — see source for full prompt]*