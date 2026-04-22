# AGENT WORKFLOW README

> ## 📚 Welkom!

Je hebt een **compleet agent-gebaseerd plan** voor VorstersNV gekregen. Dit is hoe het werkt:

---

## 🔍 Wat Je Hebt

```
📁 plan/
├──

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🎯 AGENT-GEBASEERD PLAN – VorstersNV Fase 3-5 Documentatie

## 📚 Welkom!

Je hebt een **compleet agent-gebaseerd plan** voor VorstersNV gekregen. Dit is hoe het werkt:

---

## 🔍 Wat Je Hebt

```
📁 plan/
├── 📄 AGENT_BASED_PLAN.md               ← LEES EERST
│   ├─ 3 complete use cases
│   ├─ Python code examples
│   ├─ Workflow diagrams
│   └─ Success criteria
│
├── 📄 AGENT_COMMUNICATION.md             ← LEES TWEEDE
│   ├─ Webhook architecture
│   ├─ Agent runner code
│   ├─ Error handling
│   └─ Message flow examples
│
├── 📄 ORCHESTRATION_ARCHITECTURE.md      ← LEES DERDE
│   ├─ Orchestrator class
│   ├─ Workflow YAML definitions
│   ├─ Monitoring & metrics
│   └─ Performance optimization
│
├── 📄 IMPLEMENTATION_CHECKLIST.md        ← TRACK PROGRESS
│   ├─ Week-by-week tasks
│   ├─ Success criteria
│   ├─ Risk mitigation
│   └─ Team assignments
│
├── 📄 AGENT_PLAN_SUMMARY.md             ← QUICK REFERENCE
│   ├─ Overview per phase
│   ├─ Quick start guide
│   └─ Key insights
│
└── 📄 THIS_FILE.md                      ← You are here
    └─ Navigation guide
```

---

## 🚀 Quick Start Path (30 minutes)

### Step 1: Understand Your Team (10 min)
Read this section below: **"Your 8 Agents"**

### Step 2: Understand The Workflow (10 min)
Read this: **"How It Works"** section below

### Step 3: Read First Document (10 min)
Open **AGENT_BASED_PLAN.md** and read the first section

---

## 🤖 Your 8 Agents – The Team

Your agents are the core of everything. Each specializes in one domain:

```
┌──────────────────────────────────────────────────────────┐
│  AGENT 1: Klantenservice                                │
│  ├─ Handles: Customer questions, order lookups, returns│
│  ├─ Model: llama3 (balanced)                           │
│  ├─ Speed: ~1-2 sec                                     │
│  ├─ Temperature: 0.4 (not too creative)                │
│  └─ Used by: /api/support/chat                         │
└──────────────────────────────────────────────────────────┘

┌─────

*[truncated — see source for full prompt]*