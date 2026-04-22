# Compiler Toolchain Flow

> ## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven flow for developing and validating a compiler toolchain targeting a custom processor

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Compiler Toolchain Development Flow — Full Architecture Design
## Orchestrator + Stage Agents + Skills

> **Purpose**: AI-driven flow for developing and validating a compiler toolchain targeting a custom processor ISA or embedded SoC. Covers ISA specification, compiler backend development, assembler, linker, runtime libraries, and toolchain validation. This is the software layer that enables code to run on the designed chip.

---

## 1. Architecture Overview

```
┌──────────────────────────────────────────────────────────────┐
│              COMPILER TOOLCHAIN ORCHESTRATOR                 │
│  Input:  ISA spec, processor microarch, ABI requirements     │
│  Output: Validated compiler toolchain (GCC/LLVM-based)       │
└────────────────────────┬─────────────────────────────────────┘
                         │
     ┌───────────────────┼────────────────────────────┐
     ▼                   ▼                            ▼
  ISA Spec           Backend Dev               Toolchain
  Agent              Agent                     Validation Agent
     │                   │                            │
  SKILL              SKILL                        SKILL
```

---

## 2. Shared State Object

```json
{
  "run_id": "compiler_001",
  "processor_name": "my_cpu",
  "inputs": {
    "isa_spec":          "path/to/isa.md",
    "microarch_doc":     "path/to/microarch.md",
    "base_toolchain":    "LLVM-17 | GCC-13",
    "abi_spec":          "path/to/abi.md",
    "target_triple":     "mycpu-unknown-elf",
    "register_file":     "32x 32-bit GPR + 16x 64-bit FPR",
    "endianness":        "little",
    "word_size":         32
  },
  "stages": {
    "isa_analysis":        { "status": "pending", "output": {} },
    "backend_dev":         { "status": "pending", "output": {} },
    "assembler_dev":       { "status": "pending", "output": {} },
    "linker_config":       { "status": "pending", "output": {} },
    "runtime_libs":        { "status": "pending", "output": {} },
    "toolchain_v

*[truncated — see source for full prompt]*