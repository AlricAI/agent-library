# Memory

> This guide explains how to use Mastra's memory and RAG (Retrieval-Augmented Generation) capabilities in the sample application.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory and RAG Support Guide

This guide explains how to use Mastra's memory and RAG (Retrieval-Augmented Generation) capabilities in the sample application.

## Overview

Mastra provides built-in support for:

- **Persistent Memory**: Store and retrieve conversation history across sessions
- **Working Memory**: Maintain context and key facts within a thread
- **Semantic Search**: Use vector embeddings for intelligent context retrieval
- **RAG (Retrieval-Augmented Generation)**: Enhance responses with relevant historical context
- **Knowledge Base Tools**: Query and expand a seeded knowledge base with general information

## Quick Start

### Using the Memory Agent

The sample includes a pre-configured memory agent that demonstrates these capabilities:

```bash
# Start the agent server
pnpm run dev:agent

# In another terminal, chat with the memory agent
pnpm run dev:cli -- chat memory

# Or via HTTP API
curl -X POST http://localhost:3000/api/agents/memory/generate \
  -H "Content-Type: application/json" \
  -d '{
    "messages": [{"role": "user", "content": "My name is Alice"}],
    "threadId": "user-123"
  }'

# In a new conversation with the same threadId, the agent remembers
curl -X POST http://localhost:3000/api/agents/memory/generate \
  -H "Content-Type: application/json" \
  -d '{
    "messages": [{"role": "user", "content": "What is my name?"}],
    "threadId": "user-123"
  }'
```

### Using RAG Tools

Both the **general agent** and **memory agent** come with RAG tools pre-configured:

```bash
# Ask the general agent about Mastra (it will use the knowledge base)
pnpm run dev:cli -- chat general -m "What is Mastra and what are its key features?"

# Ask about RAG implementation
pnpm run dev:cli -- chat general -m "How do I implement RAG in my application?"

# The agents will automatically query the knowledge base for accurate information
```

The knowledge base is automatically seeded with information about:

- Mastra framework and its features
- AI agent be

*[truncated — see source for full prompt]*