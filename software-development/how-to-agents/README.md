# HOW TO AGENTS

> ## 🎯 Inleiding

Dit document leert je hoe je **agents** kunt bouwen, configureren, testen en optimaliseren in het VorstersNV-platform. Agents zijn AI

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📚 How-To: Werken met Agents in VorstersNV

## 🎯 Inleiding

Dit document leert je hoe je **agents** kunt bouwen, configureren, testen en optimaliseren in het VorstersNV-platform. Agents zijn AI-gestuurde modules die automatische taken uitvoeren op basis van prompts en feedback.

---

## 📋 Inhoudsopgave

1. [Agent-Anatomie](#agent-anatomie)
2. [YAML-Configuratie](#yaml-configuratie)
3. [Prompts Schrijven](#prompts-schrijven)
4. [Agent Uitvoering](#agent-uitvoering)
5. [Testen & Debugging](#testen--debugging)
6. [Feedback-Loop & Iteratie](#feedback-loop--iteratie)
7. [Multi-Agent Orkestratie](#multi-agent-orkestratie)
8. [Best Practices](#best-practices)

---

## Agent-Anatomie

Elke agent bestaat uit **5 componenten**:

```
Agent
├── 1. YAML Config (agent definition)
├── 2. System Prompt (wat is de agent)
├── 3. Pre-prompt (context + voorbeelden)
├── 4. User Input (taak/vraag van gebruiker)
└── 5. Execution & Feedback Loop
```

### Voorbeeld Flow

```
┌─────────────────────────────────────────┐
│  User Trigger (order, webhook event)    │
└──────────┬──────────────────────────────┘
           ↓
┌──────────────────────────────────────────┐
│  Load agent YAML config                  │
│  (model, capabilities, evaluation)       │
└──────────┬───────────────────────────────┘
           ↓
┌──────────────────────────────────────────┐
│  Combine prompts:                        │
│  - System Prompt (rollen/regels)        │
│  - Pre-prompt (context/voorbeelden)     │
│  - User Input (taak)                     │
└──────────┬───────────────────────────────┘
           ↓
┌──────────────────────────────────────────┐
│  Send to Ollama LLM                      │
│  (llama3, mistral, etc)                  │
└──────────┬───────────────────────────────┘
           ↓
┌──────────────────────────────────────────┐
│  Parse & Execute Output                  │
│  (perform actions, update DB)            │
└──────────┬───────────────────────────────┘
           ↓
┌─────────────────────────

*[truncated — see source for full prompt]*