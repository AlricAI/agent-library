# Technical Brain Evolution

> **Document Version:** 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Technical Documentation: Brain Evolution Architecture

**Document Version:** 2.0  
**Last Updated:** 2026-03-29  
**Classification:** AGI Company Technical Reference

---

## Executive Summary

This document details the evolution and architecture of the AGI Company's brain systems, from the foundational SevenRegionBrain to distributed agent consciousness. The architecture prioritizes local execution, cost efficiency, and intelligent fallback chains.

---

## 1. Core Architecture Overview

### 1.1 Execution Hierarchy

```
USER REQUEST
      ↓
[1] LOCAL BRAIN (SevenRegionBrain) ← PRIMARY
      ↓ (if insufficient/confident)
[2] LOCAL MODELS (Mortimer/Ollama) ← SECONDARY
      ↓ (if needs advanced reasoning)
[3] MINIMAX API (M2.5/M2.7) ← FALLBACK ONLY
      ↓ (if API limit reached)
[4] BRAIN FALLBACK (GrowingNN local) ← FINAL
```

### 1.2 Design Principles

1. **Local First**: Brain + Mortimer handle 90%+ of tasks without external API calls
2. **Cost Optimization**: Target ~$0/month operational cost for core functionality
3. **Graceful Degradation**: Multiple fallback layers ensure continuity
4. **API Rationing**: 100 calls/day shared limit requires intelligent allocation
5. **State Persistence**: Hermes memory system maintains continuity across sessions

---

## 2. Brain Components

### 2.1 SevenRegionBrain (Primary)

The SevenRegionBrain implements an OODA (Observe-Orient-Decide-Act) loop processing model across seven functional regions:

- **Region 1**: Input normalization and context building
- **Region 2**: Pattern recognition and classification
- **Region 3**: Historical context retrieval (via Hermes)
- **Region 4**: Decision tree evaluation
- **Region 5**: Action planning and sequencing
- **Region 6**: Output generation and formatting
- **Region 7**: Feedback loop and learning capture

**Confidence Thresholds:**
- `>0.8`: Direct response, no fallback needed
- `0.5-0.8`: Local model enhancement (Mortimer)
- `<0.5`: Advanced reasoning required (MiniMax fallback)


*[truncated — see source for full prompt]*