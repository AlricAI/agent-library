# MASTER INDEX

> ## Complete Agent + Skill Architecture for Chip Design

> **Purpose**: This document is the master index for the full digital design pipeline. It maps

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Digital Design & Software Pipeline — Master Index
## Complete Agent + Skill Architecture for Chip Design

> **Purpose**: This document is the master index for the full digital design pipeline. It maps every flow document to its position in the end-to-end chip design process and defines how orchestrators hand off to each other across the complete design journey from specification to tape-out and firmware.

---

## Full Pipeline Overview

```
                     ┌─────────────────────────────────────────────────────┐
                     │          0. INFRASTRUCTURE SETUP                    │
                     │  Tool detection, wrappers, MCP config               │
                     └────────────────────┬────────────────────────────────┘
                                          │
                     ┌────────────────────▼────────────────────────────────┐
                     │             PRODUCT SPECIFICATION                   │
                     └────────────────────┬────────────────────────────────┘
                                          │
                     ┌────────────────────▼────────────────────────────────┐
                     │  1. ARCHITECTURE EVALUATION                         │
                     │     Microarch doc, PPA estimates, risk register      │
                     └────────────────────┬────────────────────────────────┘
                                          │
               ┌──────────────────────────┼──────────────────────────┐
               ▼                          ▼                          ▼
    ┌──────────────────┐      ┌───────────────────┐      ┌──────────────────────┐
    │ 2. RTL DESIGN    │      │ 3. HLS FLOW        │      │ 7. FPGA EMULATION    │
    │ SV coding, lint, │      │ C/C++ → RTL        │      │ Early SW bring-up    │
    │ CDC, synth check │      │ (for algo blocks)  │      │ (runs in parallel)   │
    └────────┬─────────┘      └─────────┬──────────┘      └──────────────────────┘
             │   

*[truncated — see source for full prompt]*