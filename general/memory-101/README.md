# MEMORY

> ## Overview

The Agent Lab memory module provides a comprehensive conversation memory system with both **short-term** and **long-term** memory capabil

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory Module Guide

## Overview

The Agent Lab memory module provides a comprehensive conversation memory system with both **short-term** and **long-term** memory capabilities. Built on **LangGraph** and **LangChain** with hybrid storage (MySQL + Pinecone), it supports multiple memory types:

- **Short-term Memory**: Recent conversation buffer using LangGraph state management
- **Semantic Memory**: Facts and knowledge extracted from conversations (hybrid storage)
- **Episodic Memory**: Temporal summaries of conversation episodes
- **Profile Memory**: Aggregated user characteristics and preferences
- **Procedural Memory**: Identified interaction patterns and workflows

## Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    IntegratedMemoryService                          │
│  (Unified interface combining short-term and long-term memory)      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌────────────────────────────┐  ┌───────────────────────────────┐ │
│  │  ShortTermMemoryService    │  │  LongTermMemoryProcessor      │ │
│  │                            │  │                               │ │
│  │  - Buffer Memory           │  │  - Semantic Extraction        │ │
│  │  - Window Memory           │  │  - Profile Building           │ │
│  │  - Summary Memory          │  │  - Episodic Summarization     │ │
│  │                            │  │  - Pattern Recognition        │ │
│  │  Backend: MySQL + SQLite   │  │  Backend: MySQL + Pinecone    │ │
│  └────────────────────────────┘  └───────────────────────────────┘ │
│                                                                      │
│  Storage Layer:                                                      │
│  - MySQL (chat_history table) - Structured conversation data        │
│  - SQLite (checkpoints) - Session state persistence                 │
│  - Pine

*[truncated — see source for full prompt]*