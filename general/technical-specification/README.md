# TECHNICAL SPECIFICATION

> ## Skills-First Cognitive Architecture v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AOS Brain: Technical Specification
## Skills-First Cognitive Architecture v1.0

---

## 1. System Overview

### 1.1 Core Components

```
┌─────────────────────────────────────────────────────────────┐
│                      SKILL ORCHESTRATOR                     │
├─────────────────────────────────────────────────────────────┤
│  OODA Loop (Observe → Orient → Decide → Act)              │
│  └─ Coordinates via SkillRegistry                         │
├─────────────────────────────────────────────────────────────┤
│  Skill Registry                                             │
│  ├─ Contract validation                                   │
│  ├─ Version management                                      │
│  ├─ Routing to handlers                                   │
│  └─ Performance tracking                                  │
├─────────────────────────────────────────────────────────────┤
│  Region Consumers (thin wrappers)                         │
│  ├─ ThalamusRegion → SKILL:thalamus-v1                  │
│  ├─ PFCRegion → SKILL:pfc-v2                            │
│  └─ ...                                                   │
├─────────────────────────────────────────────────────────────┤
│  Self-Diagnostics                                           │
│  ├─ Health check (every 100 ticks)                        │
│  ├─ Auto-recovery (tick-recovery skill)                   │
│  └─ GrowingNN tuning                                      │
└─────────────────────────────────────────────────────────────┘
```

### 1.2 Data Flow

```
Input (Observation)
    ↓
[SKILL:thalamus-v1] → Normalization + Routing
    ↓
[SKILL:pfc-v2] → Decision-making
    ↓
Output (Action)
    ↓
Health Check (every 100 ticks)
```

---

## 2. Skill Specification

### 2.1 Skill File Structure

```
skills/
└── {skill-name}-v{version}/
    ├── SKILL.md          # Contract + documentation
    ├── handler.py        # Implementation
    └── schema.json       # JSON Schema (optional)
```

### 2.2 SKILL.md Format

*[truncated — see source for full prompt]*