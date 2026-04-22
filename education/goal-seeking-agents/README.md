# GOAL SEEKING AGENTS

> A complete guide to generating, evaluating, and iterating on autonomous learning agents in amplihack.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Goal-Seeking Agents

A complete guide to generating, evaluating, and iterating on autonomous learning agents in amplihack.

---

## Table of Contents

- [What Are Goal-Seeking Agents?](#what-are-goal-seeking-agents)
- [Quick Start](#quick-start)
- [Generating Agents](#generating-agents)
- [Agent Capabilities](#agent-capabilities)
- [Architecture](#architecture)
- [Multi-Agent Architecture](#multi-agent-architecture)
- [Evaluating Agents](#evaluating-agents)
- [Iterating on Agents](#iterating-on-agents)
- [Domain Agents](#domain-agents)
- [Current Scores](#current-scores)
- [Reference](#reference)

---

## What Are Goal-Seeking Agents?

Goal-seeking agents are autonomous programs that pursue objectives by learning, reasoning, and taking actions. Unlike static scripts that follow a fixed sequence, these agents:

1. **Learn** -- Extract facts from content and store them in persistent memory.
2. **Remember** -- Search, verify, and organize knowledge across sessions.
3. **Teach** -- Explain what they know to other agents (or humans) through multi-turn dialogue.
4. **Apply** -- Use stored knowledge and tools to solve new problems.

The system provides a single `GoalSeekingAgent` base class that works identically across four different SDK backends (Copilot, Claude, Microsoft Agent Framework, and a lightweight mini-framework). You write your agent logic once; the SDK handles the underlying LLM calls, tool registration, and agent loop.

**Core design**: The `GoalSeekingAgent` ABC defines the interface. All SDK implementations delegate learning and answering to a shared `LearningAgent` instance, which contains the eval intelligence: LLM-based fact extraction, intent detection, retrieval strategy selection, and answer synthesis. This means every SDK gets the same quality of fact extraction and question answering regardless of the underlying LLM provider.

### LearningAgent contributor docs

Use these pages when you are working on the refactored `LearningAgent` internals:

- 

*[truncated — see source for full prompt]*