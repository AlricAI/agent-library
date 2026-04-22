# User Manual

> ## Table of Contents

1. [What is Agentic.NET?](#1-what-is-agenticnet)
2. [Prerequisites](#2-prerequisites)
3. [Installation](#3-installation)
4. [Cor

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agentic.NET — User Manual

## Table of Contents

1. [What is Agentic.NET?](#1-what-is-agenticnet)
2. [Prerequisites](#2-prerequisites)
3. [Installation](#3-installation)
4. [Core concepts](#4-core-concepts)
5. [Quick start — minimal chat agent](#5-quick-start--minimal-chat-agent)
6. [Streaming](#6-streaming)
7. [Memory — giving your agent a past](#7-memory--giving-your-agent-a-past)
8. [Tools — letting the agent act](#8-tools--letting-the-agent-act)
9. [Middleware — intercepting the pipeline](#9-middleware--intercepting-the-pipeline)
10. [Agent identity with SOUL.md](#10-agent-identity-with-soulmd)
11. [Agent skills](#11-agent-skills)
12. [Semantic memory with embeddings](#12-semantic-memory-with-embeddings)
13. [Custom chat clients](#13-custom-chat-clients)
14. [OpenTelemetry observability](#14-opentelemetry-observability)
15. [AgentBuilder reference](#15-agentbuilder-reference)
16. [Namespace reference](#16-namespace-reference)
17. [Environment variables](#17-environment-variables)
18. [Common patterns and recipes](#18-common-patterns-and-recipes)
19. [Troubleshooting](#19-troubleshooting)

---

## 1. What is Agentic.NET?

Agentic.NET is an open-source .NET library for building AI assistants (agents) that can hold conversations, remember past interactions, call external tools, and carry a defined identity — all through a clean, composable API.

It is **not** a prompt-engineering framework and **not** a cloud service. It is a lightweight runtime that sits between your application code and any Large Language Model (LLM) backend. You bring the API key; the library wires everything together.

**What it gives you out of the box:**

| Feature | Description |
|---|---|
| Conversation loop | Multi-turn chat with automatic history management |
| Tool calling | The model can request and execute functions you define |
| Memory | Store and retrieve past messages (keyword or semantic search) |
| Middleware pipeline | Insert logic before and after every LLM call |
| Agent ide

*[truncated — see source for full prompt]*