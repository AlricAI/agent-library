# 02 Architecture

> Python/FastAPI agent server architecture with Pydantic AI and LiteLLM

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Server Architecture

## Overview

The agent server is a Python/FastAPI application that provides AI agent execution, tool orchestration, workflow management, and intelligent query routing. It uses Pydantic AI for agent management and integrates with LiteLLM for LLM access.

## System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      Agent Client (Next.js)                  │
│                    Browser / React UI                        │
└────────────────────────┬────────────────────────────────────┘
                         │ HTTP/REST + SSE
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                    Agent Server (FastAPI)                    │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              API Layer (FastAPI)                      │  │
│  │  /runs, /agents, /dispatcher, /workflows, /scores    │  │
│  └──────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              Service Layer                            │  │
│  │  RunService, AgentRegistry, DispatcherService,       │  │
│  │  TokenService, Scheduler, ScorerService              │  │
│  └──────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              Agent Layer (Pydantic AI)                │  │
│  │  chat_agent, rag_agent, search_agent, dispatcher     │  │
│  └──────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              Tool Layer                               │  │
│  │  search_tool, ingest_tool, rag_tool, weather_tool    │  │
│  └──────────────────────────────────────────────────────┘  │
└────────────────────────┬────────────────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         │             

*[truncated — see source for full prompt]*