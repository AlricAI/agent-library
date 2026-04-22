# 23 Mcp Servers Agent Runtime

> ## Context

You are working on the MCP (Model Context Protocol) and agent runtime packages for crypto-vision. These packages allow AI assistants (Clau

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 23 — MCP Servers & Agent Runtime Packages

## Context

You are working on the MCP (Model Context Protocol) and agent runtime packages for crypto-vision. These packages allow AI assistants (Claude, ChatGPT plugins, etc.) to access crypto data tools:

### Package Inventory

1. **`packages/mcp-server/`** — Main MCP server with 24 tool modules:
   - Modules: `ai-predictions/`, `ai-prompts/`, `alerts/`, `coingecko/`, `defi/`, `dex-analytics/`, `governance/`, `historical-data/`, `indicators/`, `lyra-ecosystem/`, `market-data/`, `news/`, `portfolio/`, `pump-fun/`, `research/`, `rubic/`, `server-utils/`, `social/`, `token-unlocks/`, `tool-marketplace/`, `tradingview/`, `utils/`, `wallet-analytics/`, `websockets/`
   - Entry: `index.ts`, CLI via `cli.ts`
   - Server: Express-based MCP server
   - Types: `types/` directory

2. **`packages/binance-mcp/`** — Binance-specific MCP server:
   - `src/` — Binance API tools (spot, futures, margin)
   - `binance-mcp-server/` — Server implementation
   - `binance-us-mcp-server/` — Binance US variant
   - Docs, config, test tools

3. **`packages/bnbchain-mcp/`** — BNB Chain MCP server:
   - `src/` — BNB Chain tools (BEP-20, DEX, BSC explorer)
   - Similar structure to binance-mcp

4. **`packages/agent-runtime/`** — ERC-8004 agent runtime:
   - `src/agent.ts` — Core agent implementation
   - `src/server.ts` — Runtime server
   - `src/main.ts` — Entry point
   - `src/protocols/a2a/` — Agent-to-Agent protocol
   - `src/protocols/erc8004/` — ERC-8004 on-chain agent registry
   - `src/protocols/x402/` — x402 payment protocol
   - `src/discovery/` — Agent discovery (connect, search, wellKnown)
   - `src/middleware/` — Runtime middleware
   - `src/utils/` — Utilities
   - Docker + docker-compose for deployment

## Task

### 1. Audit & Fix `packages/mcp-server/`

For each of the 24 modules, verify:
- **Tool definitions** are valid MCP tool schemas (name, description, inputSchema)
- **Handlers** make real API calls to the crypto-vision 

*[truncated — see source for full prompt]*