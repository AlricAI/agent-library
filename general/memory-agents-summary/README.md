# MEMORY AGENTS SUMMARY

> **Architecture Version:** 1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory-Enabled Goal-Seeking Agents: Executive Summary

**Architecture Version:** 1.0
**Date:** 2026-02-14
**Status:** ✅ Design Complete - Ready for Implementation

---

## What We're Building

**Memory-enabled goal-seeking agents** that learn from experience and improve over time. Each agent accumulates knowledge across sessions, enabling future executions to be faster, more accurate, and more effective.

**Key Innovation:** Agents remember what they learned and apply that knowledge in future sessions, demonstrating measurable improvement (20-30% faster, 10-20% more accurate).

---

## Design Documents

| Document                                  | Purpose                       | Pages       |
| ----------------------------------------- | ----------------------------- | ----------- |
| **MEMORY_ENABLED_AGENTS_ARCHITECTURE.md** | Complete system specification | 87 pages    |
| **MEMORY_AGENTS_DIAGRAMS.md**             | Visual architecture diagrams  | 10 diagrams |
| **MEMORY_AGENTS_SUMMARY.md** (this file)  | Executive summary             | 4 pages     |

---

## System Components

### 1. amplihack-memory-lib (Standalone Package)

**Purpose:** Shared memory infrastructure for all agents

**Key Features:**

- Graph-based knowledge storage (Kuzu database)
- Episodic memory (what happened)
- Semantic memory (what learned)
- Code graph queries (codebase structure)
- Security wrapper (capability-based access control)

**API:**

```python
from amplihack_memory import MemoryClient, AgentCapabilities

memory = MemoryClient(db_path, capabilities)
memory.record_experience("action", "Analyzed file auth.py")
memory.extract_knowledge("SQL injection", "String concat is vulnerable")
learnings = memory.retrieve_knowledge("SQL injection patterns")
```

**Installation:**

```bash
pip install amplihack-memory-lib
```

---

### 2. Enhanced Goal Agent Generator

**Purpose:** Generate agents with memory capabilities injected

**New Features:**

- `--memory-enabled` flag for agent gener

*[truncated — see source for full prompt]*