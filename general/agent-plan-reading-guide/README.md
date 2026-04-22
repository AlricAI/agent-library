# AGENT PLAN READING GUIDE

> ## 🗺️ Plan Structure Visualized

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VorstersNV Agen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📚 READING GUIDE – Agent-Based Plan Overview

## 🗺️ Plan Structure Visualized

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VorstersNV Agent-Based Plan (Complete)               │
└─────────────────────────────────────────────────────────────────────────┘
                                    │
                        ┌───────────┴────────────┐
                        │                        │
        ┌───────────────▼────────┐  ┌───────────▼────────────┐
        │   ENTRY POINT          │  │   EXISTING DOCS        │
        │                        │  │   (Reference)          │
        ├────────────────────────┤  ├────────────────────────┤
        │ • Workflow README      │  │ • PLAN.md              │
        │ • Plan Summary         │  │ • Cloud Project Plan   │
        │ • INDEX (this file)    │  │ • Technical Impl       │
        │ • Checklist            │  │ • Execution Roadmap    │
        └────────────┬───────────┘  │ • MCP Agents           │
                     │              │ • Fase 4 Docs          │
                     │              └────────────────────────┘
                     │
        ┌────────────▼─────────────────────┐
        │   CORE PLANNING DOCUMENTS         │
        ├───────────────────────────────────┤
        │ 1. AGENT_BASED_PLAN.md            │
        │    (What to build + code)         │
        │                                   │
        │ 2. AGENT_COMMUNICATION.md         │
        │    (How agents talk)              │
        │                                   │
        │ 3. ORCHESTRATION_ARCHITECTURE.md  │
        │    (How system works)             │
        └───────────────────────────────────┘
```

---

## 📖 Reading Sequence

### Your Role Matters!

#### 👨‍💼 For Project Managers (30 min)
```
Start
  │
  ▼
AGENT_WORKFLOW_README.md ────► AGENT_PLAN_SUMMARY.md
(Get Overview)                (See Timeline)
  │
  └──────────┬─────────────────────────────────┐
           

*[truncated — see source for full prompt]*