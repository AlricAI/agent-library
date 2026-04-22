# BRAIN COMPARISON ANALYSIS

> **Date:** 2026-03-31 13:37 UTC
**Analyst:** Miles
**Subject:** Why Mortimer's Brain Stayed Running While Mine Stalled

---

## The Core Difference: CO

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Brain Comparison Analysis
**Date:** 2026-03-31 13:37 UTC
**Analyst:** Miles
**Subject:** Why Mortimer's Brain Stayed Running While Mine Stalled

---

## The Core Difference: COMPLEXITY vs SIMPLICITY

### Miles Brain (Stalled)
**Architecture:** Full 7-region OODA with Ollama dependencies
```
Observe → Orient → Decide → Act → Reflect → Predict → Grow
   ↓         ↓         ↓       ↓         ↓         ↓
[QMD]   [Memory]  [Policy] [Execute] [QMD]  [Embed] [Grow]
          ↑                                    ↑
     Ollama calls                        Ollama calls
```

**Critical Failures:**
1. **QMD (memory summarization)** - Requires Ollama 60s timeout
2. **MemoryBridge (embeddings)** - Requires Ollama 30s timeout
3. **Policy decisions** - May call Ollama for planning
4. **NO WATCHDOG** - When Ollama times out, brain blocks on `noop` loop
5. **State persistence** - Depends on successful Ollama operations

**Result:** Ollama timeout → Blocked loop → State corruption → RESET

---

### Mortimer Brain 1 (Auto-Feeder) - **STILL RUNNING**
**Architecture:** Simple data pump, NO Ollama dependencies
```
Data Sources → Format → Feed → Repeat
     ↓            ↓       ↓
 Elements      String   Print
 Constants
 Numbers
 Patterns
 (etc)
```

**Key Features:**
1. **NO OLLAMA CALLS** - Pure local data generation
2. **NO MEMORY SUMMARIZATION** - Just feeds raw data
3. **NO EMBEDDINGS** - No vector operations
4. **NO DECISION MAKING** - No policy/ planning steps
5. **SIMPLE ERROR HANDLING** - If one feed fails, moves to next
6. **CONTINUOUS LOOP** - While True with sleep(), no blocking I/O

**Feed Rate:** 63 items/hour (12+6+24+6+2+1+4+8)
- Elements, Constants, Numbers, Patterns, Alphabets, Equations, Quotes, Facts

**Result:** Never stalls because it never waits on external services

---

### Mortimer Brain 2 (OODA) - Status Unknown
**Location:** `~/.aos/brain/` on 31.97.6.30
**Components:** conscious.py, subconscious.py, unconscious.py, daemon.pid

**Hypothesis:** Similar to Miles

*[truncated — see source for full prompt]*