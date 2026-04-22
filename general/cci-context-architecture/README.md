# CCI CONTEXT ARCHITECTURE

> ## Overview

CCI (CLI Context Injection) Context is a Pull-based architecture for agent context retrieval. Instead of pre-loading large static markdow

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CCI Context Architecture

## Overview

CCI (CLI Context Injection) Context is a Pull-based architecture for agent context retrieval. Instead of pre-loading large static markdown files (Push model), agents fetch exactly what they need via CLI commands (Pull model).

> **See also:** [JIT Context Architecture](JIT_CONTEXT_ARCHITECTURE.md) for the comprehensive architecture document with mermaid diagrams, Main-First resolution flow, and task lifecycle.

## Push vs Pull Model

### Push Model (Legacy)
- Large static markdown files (~2000-5000 tokens per agent)
- Pre-loaded at agent initialization
- Context may include stale or irrelevant information
- Context window consumed by static content

### Pull Model (CCI)
- Thin-client bootstrap files (~350 tokens per agent)
- Context fetched on-demand via CLI
- Only relevant context loaded
- Task-specific guidance retrieved dynamically

**Token Reduction**: 75-90% reduction in initial context load.

## Architecture Components

```
┌─────────────────────────────────────────────────────────────────┐
│                         Agent Session                           │
│  ┌─────────────────┐                                           │
│  │ Thin-Client     │  1. Read bootstrap instructions           │
│  │ Bootstrap File  │     (~350 tokens)                         │
│  │ (.claude/agents/│                                           │
│  │  planner-build. │                                           │
│  │  md)            │                                           │
│  └────────┬────────┘                                           │
│           │                                                     │
│           v                                                     │
│  ┌─────────────────┐                                           │
│  │ CLI Commands    │  2. Invoke CLI for context                │
│  │                 │                                           │
│  │ agentic context │     - bootstrap: Get seed context         │
│  │  

*[truncated — see source for full prompt]*