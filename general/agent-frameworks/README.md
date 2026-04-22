# AGENT FRAMEWORKS

> _Received from Omar — 2026-03-29 03:45 UTC_

---

## 1. OmniMemory — The Living Brain

**Type:** Memory system for autonomous agents
**Language:** Pyt

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Framework Collection

_Received from Omar — 2026-03-29 03:45 UTC_

---

## 1. OmniMemory — The Living Brain

**Type:** Memory system for autonomous agents
**Language:** Python 3.10+
**Repo:** omnirexflora-labs/omnimemory

### Key Features
- **Dual-Agent Synthesis** — Episodic + Summarizer agents process memories
- **Self-Evolving** — Update/Delete/Skip operations when memories conflict
- **Composite Scoring** — Relevance × [1 + Recency + Importance]
- **Structured Memory Notes** — Behavior, Learnings, Guidance
- **Docker ready** — Dockerfile + docker-compose.local.yml

### vs Traditional RAG
| Feature | Traditional RAG | OmniMemory |
|---------|----------------|------------|
| Input | Naive chunking | Dual-Agent Synthesis |
| Conflicts | None (coexist) | Self-Evolving resolution |
| Retrieval | Cosine similarity | Composite scoring |
| Context | Static chunks | Structured memory notes |

### Use for Lord Sav
- Replace basic memory with self-evolving cognitive substrate
- Automatic conflict resolution
- Importance-weighted recall

---

## 2. OmniCoreAgent — Production Agent Framework

**Type:** AI Agent Framework for production
**Language:** Python 3.10+
**Features:**
- Runtime memory backend switching
- Automatic context management
- Tool output guardrails
- Tool response offloading
- Community tools support

### Use for Lord Sav
- Production-ready agent architecture
- Runtime flexibility for memory backends
- Tool safety guardrails

---

## 3. Swarm — Multi-Agent Orchestration

**Type:** OpenAI's experimental multi-agent framework
**Note:** Now replaced by OpenAI Agents SDK
**Language:** Python 3.10+

### Core Concepts
- Agents hand off to other agents
- Lightweight, educational
- Function-calling based handoffs

### Use for Lord Sav
- Multi-agent coordination patterns
- Agent handoff architecture
- Reference for swarm-style deployments

---

## 4. Workflow Orchestrator (Agent Role)

**Role:** Design explicit stage workflows for complex tasks
**Model:** gpt

*[truncated — see source for full prompt]*