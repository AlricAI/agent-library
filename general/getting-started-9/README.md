# Getting Started

> Welcome to the Mastra TypeScript starter template!

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started with Mastra

Welcome to the Mastra TypeScript starter template! This guide will help you understand how Mastra works by default and get you up and running quickly.

## What is Mastra?

Mastra is a TypeScript framework for building AI agents and workflows. This starter template demonstrates all core Mastra concepts in a ready-to-use application.

## How It Works By Default

### 1. **Agent Networks** - The Core Pattern

Mastra uses an **agent network** pattern where a **router agent** intelligently delegates tasks to specialized agents:

```
User Request → Router Agent → [General Agent | Weather Agent | Memory Agent]
                    ↓
              LLM analyzes request
                    ↓
           Selects best specialist
                    ↓
            Returns their response
```

**How it works:**
- The router agent receives your request
- It uses GPT-4o-mini to analyze which specialist can best help
- It delegates to that agent and returns their response
- All coordination happens automatically

### 2. **Storage** - LibSQL by Default

Out of the box, Mastra uses **LibSQL** (a file-based SQLite variant):

- **Location**: `./data/app.db`
- **Setup**: Zero configuration required
- **Perfect for**: Development, testing, prototyping
- **Stores**: Conversation threads, knowledge base, vectors

**Why LibSQL?**
- No database server needed
- Automatic creation on first run
- Easy to reset: just delete `data/app.db`
- Supports vector operations for RAG

### 3. **Memory & RAG** - Built-in Knowledge

The template includes **automatic knowledge base seeding**:

**On server startup:**
1. Mastra checks if knowledge base exists
2. If not, it loads markdown files from `/knowledge` directory
3. Documents are chunked, embedded, and stored
4. Agents can now search this knowledge via RAG tools

**Knowledge included by default:**
- BioSynth Corporation research
- Quantum Flux Capacitor technology
- Graviton Wave Theory

**How agents use it:**
- Agents have `que

*[truncated — see source for full prompt]*