# ARCHITECTURE

> > System architecture for the `crypto-vision` monorepo — a comprehensive cryptocurrency intelligence platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture

> System architecture for the `crypto-vision` monorepo — a comprehensive cryptocurrency intelligence platform.

## Table of Contents

1. [System Overview](#system-overview)
2. [High-Level Architecture](#high-level-architecture)
3. [Monorepo Structure](#monorepo-structure)
4. [Core API Service](#core-api-service)
5. [Data Pipeline](#data-pipeline)
6. [AI & Intelligence Layer](#ai--intelligence-layer)
7. [Agent System](#agent-system)
8. [Pump Agent Swarm](#pump-agent-swarm)
9. [Frontend Applications](#frontend-applications)
10. [Infrastructure](#infrastructure)
11. [Inter-Service Communication](#inter-service-communication)
12. [Security Architecture](#security-architecture)

---

## System Overview

Crypto Vision is a multi-layered cryptocurrency intelligence platform comprising:

- **Core API** — Hono-based REST API aggregating data from 37+ upstream sources
- **Data Pipeline** — ingestion workers that normalize and warehouse market/DeFi/news data into BigQuery
- **AI Layer** — multi-provider LLM integration (Groq, Gemini, OpenAI, Anthropic, OpenRouter) with RAG, embeddings, and fine-tuned models
- **Agent System** — 43 specialized DeFi AI agents accessible via REST API
- **Pump Agent Swarm** — autonomous multi-agent swarm for Solana Pump.fun token lifecycle
- **MCP Servers** — Model Context Protocol servers exposing Binance, BNB Chain, and crypto intelligence tools to AI assistants
- **Frontend Apps** — Next.js dashboard, news aggregator, and Remotion video renderer
- **Infrastructure** — Terraform, Kubernetes, Cloud Run, BigQuery, Pub/Sub on GCP (portable to self-hosted)

---

## High-Level Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                        CLIENTS                                   │
│  Dashboard (Next.js)  │  News App  │  Telegram Bot  │  MCP AI   │
└──────────┬────────────┴─────┬──────┴───────┬────────┴─────┬─────┘
           │                  │              │              │
          

*[truncated — see source for full prompt]*