# PACKAGES

> > Standalone packages in the `crypto-vision` monorepo — independently publishable to npm.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Packages

> Standalone packages in the `crypto-vision` monorepo — independently publishable to npm.

## Overview

The `packages/` directory contains 8 standalone packages. Each has its own `package.json`, `tsconfig.json`, build pipeline, and tests. Packages are **not** tightly coupled to the root API — they can be published and used independently.

| Package | npm Name | Purpose | Stack |
|---------|----------|---------|-------|
| [agent-runtime](#agent-runtime) | `@nirholas/erc8004-agent-runtime` | ERC-8004 agent runtime with A2A + x402 payments | Hono, ethers.js |
| [binance-mcp](#binance-mcp) | `@nirholas/binance-mcp-server` | Binance MCP server (478+ tools) | MCP SDK, Binance SDKs |
| [bnbchain-mcp](#bnbchain-mcp) | `@nirholas/bnbchain-mcp` | BNB Chain MCP server (384 tools) | MCP SDK, viem |
| [market-data](#market-data) | `@nirholas/crypto-market-data` | Standalone market data library | Zero deps, native fetch |
| [mcp-server](#mcp-server) | `@crypto-vision/mcp-server` | Crypto Vision MCP server | MCP SDK, Solana web3 |
| [pump-agent-swarm](#pump-agent-swarm) | `@nirholas/pump-agent-swarm` | Pump.fun multi-agent swarm | Solana, pump-sdk |
| [sweep](#sweep) | `sweep` | Multi-chain dust sweeper | ethers, viem, BullMQ |
| [ucai](#ucai) | `abi-to-mcp` (Python) | Universal Contract AI Interface | Python, web3.py |

---

## agent-runtime

**Package:** `@nirholas/erc8004-agent-runtime`
**Location:** `packages/agent-runtime/`

Build AI agents with on-chain identity, inter-agent communication, and pay-per-request monetization.

### Features

- **ERC-8004 on-chain identity** — agents have verifiable blockchain identities
- **A2A protocol** — Google's Agent-to-Agent messaging standard for inter-agent communication
- **x402 micropayments** — HTTP 402-based pay-per-request pricing with USDC
- **`.well-known/agent.json` discovery** — automatic agent discovery endpoint
- **Hono HTTP server** — lightweight agent HTTP interface

### Structure

```
src/
├── agent.ts          

*[truncated — see source for full prompt]*