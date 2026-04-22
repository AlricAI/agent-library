# Memory System

> ## Overview

Koan's memory system captures project knowledge that is not derivable
from code. It prevents LLM agents from repeating mistakes, re-deriv

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Koan Memory System — Specification v4

## Overview

Koan's memory system captures project knowledge that is not derivable
from code. It prevents LLM agents from repeating mistakes, re-deriving
settled questions, and drifting from established architectural choices
across workflow runs.

The memory system consists of markdown files stored in `.koan/memory/`
within the project repository. These files are version-controlled
alongside the project's source code, human-readable, and maintained
by koan's LLM agents with explicit user review. A retrieval layer
indexes these files and provides hybrid search (semantic + keyword)
for koan's agents to query during workflows.

Every memory entry is a single markdown file with YAML frontmatter
carrying structured metadata and a prose body written in event-style.
This design makes each entry independently retrievable, independently
reviewable, and independently trackable via version control.

### What this is not

This is not conversational memory. Systems like Mem0, SimpleMem,
Hindsight, and A-Mem extract and consolidate facts from dialogue
streams. Their benchmarks (LoCoMo, LongMemEval) test recall of
conversational facts across sessions.

Koan's memory is fundamentally different:

- **Deliberate, not extracted.** Entries are proposed by the
  orchestrator agent and approved by the human user during a
  curation workflow. Every entry is human-reviewed before it enters
  memory.

- **Structured, not atomic.** Each entry is 100–500 tokens of
  self-contained prose — an architectural decision with rationale
  and alternatives, not an atomic fact like "user prefers coffee."
  The grain size is justified by EMem's neo-Davidsonian argument:
  relational knowledge must stay bundled (Zhou et al., 2025).

- **The producer and consumer are LLMs.** The primary reader of
  memory entries is the intake agent at the start of the next
  workflow. The human oversees (reviews proposals, approves entries)
  but does not browse or query memory di

*[truncated — see source for full prompt]*