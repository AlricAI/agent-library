# REPOSITORY GUIDE

> This guide documents the full `crypto-vision` repository structure and how the major projects relate to each other.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Crypto Vision Repository Guide

This guide documents the full `crypto-vision` repository structure and how the major projects relate to each other.

## 1) What this repository contains

`crypto-vision` is a multi-project TypeScript monorepo-style workspace containing:

- A root API service (Hono + TypeScript) for crypto intelligence and AI endpoints
- Multiple app surfaces under `apps/` (`dashboard`, `news`, `video`)
- Reusable and standalone packages under `packages/`
- Infrastructure-as-code and deployment resources under `infra/`
- Prompt and agent assets under `prompts/` and `agents/`
- Multi-layer test suites under `tests/`

## 2) High-level repository map

```text
crypto-vision/
├── src/                    # Root API service implementation
├── tests/                  # Root service tests (e2e, integration, fuzz, load)
├── apps/
│   ├── dashboard/          # Next.js dashboard product
│   ├── news/               # Next.js news-focused product
│   └── video/              # Remotion video project
├── packages/
│   ├── agent-runtime/      # Agent runtime package
│   ├── binance-mcp/        # Binance MCP server package
│   ├── bnbchain-mcp/       # BNB Chain MCP package
│   ├── market-data/        # Market data package
│   ├── mcp-server/         # Main MCP server package
│   ├── pump-agent-swarm/   # Pump.fun swarm orchestration package
│   ├── sweep/              # Sweep protocol/contracts + frontend
│   └── ucai/               # Universal Contract AI Interface package
├── infra/                  # Deployment and cloud infra resources
├── agents/                 # Agent catalog, templates, docs, locales, prompts
├── prompts/                # System prompts + swarm prompt packs
├── docs/                   # Root operational and architecture docs
└── scripts/                # Data export/import and helper scripts
```

## 3) Root API service (`src/`)

The root service is the primary backend API and includes:

- Market endpoints
- DeFi endpoints
- News endpoints
- O

*[truncated — see source for full prompt]*