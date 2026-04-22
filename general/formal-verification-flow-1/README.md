# Formal Verification Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven formal verification flow covering formal property verification (FPV), logical equiva

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Formal Verification Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven formal verification flow covering formal property verification (FPV), logical equivalence checking (LEC), and CDC/RDC formal analysis. Complements simulation-based verification for exhaustive proof of correctness.

---

## 1. Shared State Object

```json
{
  "run_id": "formal_001",
  "design_name": "my_block",
  "inputs": {
    "rtl_filelist":  "filelist.f",
    "properties":    "properties.sva",
    "assumptions":   "assumptions.sva",
    "golden_netlist": "rtl.v",
    "revised_netlist": "netlist.v"
  },
  "stages": {
    "property_planning":   { "status": "pending", "output": {} },
    "environment_setup":   { "status": "pending", "output": {} },
    "fpv_run":             { "status": "pending", "output": {} },
    "cex_analysis":        { "status": "pending", "output": {} },
    "lec_run":             { "status": "pending", "output": {} },
    "formal_signoff":      { "status": "pending", "output": {} }
  },
  "properties": {
    "proven": [], "failed": [], "vacuous": [], "inconclusive": []
  },
  "lec_result": null,
  "flow_status": "not_started"
}
```

---

## 2. Stage Sequence

```
[Property Planning] ──► [Environment Setup] ──► [FPV Run]
                                                     │ CEX found
                                                     ▼
                                              [CEX Analysis]
                                                     │ RTL bug → fix RTL
                                                     │ assumption issue → fix env
                                                     └──────► [FPV Run] (retry)
                                                     │ all proven
                              ▼
                          [LEC Run] ──► [Formal Sign-off]
                              │ unmatched points → fix netlist
                              └──────► [LEC Run] (retry)
```

### Loop-Back Rules


*[truncated — see source for full prompt]*