# AGENTS

> > 58 production-ready AI agents for DeFi, portfolio management, trading, and Web3 workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Agents

> 58 production-ready AI agents for DeFi, portfolio management, trading, and Web3 workflows.

## Overview

Crypto Vision ships with **58 specialized AI agents**, each designed for a specific domain of cryptocurrency intelligence. Agents are defined as declarative JSON files with system prompts, few-shot examples, and metadata — they are runtime-agnostic and served as static JSON from a CDN.

| | |
|---|---|
| **Package** | `@nirholas/ai-agents-library` v1.42.0 |
| **Location** | `agents/` |
| **CDN** | `https://sperax.click/` (GitHub Pages) |
| **MCP Server** | `io.github.nirholas/defi-agents` (stdio transport) |
| **Languages** | 18 locales with AI-powered translation |

## Architecture

```
agents/
├── src/                        # Agent source definitions (English)
├── locales/                    # Auto-translated locale files (18 languages)
├── prompts/                    # System prompts per agent
├── schema/                     # JSON Schema validation (draft-07)
│   └── speraxAgentSchema_v1.json
├── scripts/                    # Build / i18n / validation pipeline
├── docs/                       # Detailed agent guides (14 docs)
├── agents-manifest.json        # Full agent registry
├── agent-template.json         # Template for creating new agents
├── agent-template-full.json    # Extended template
├── meta.json                   # Package metadata
├── server.json                 # MCP server configuration
├── AGENTS.md                   # Agent development guidelines
├── CHANGELOG.md                # Version history
├── CONTRIBUTING.md             # Contribution guide
└── LICENSE                     # MIT license
```

**Key design principle:** Agent definitions are **data, not code**. The `agents/` directory is purely declarative; the `packages/agent-runtime/` package provides the execution engine.

---

## Agent Categories

| Category | Count | Description |
|----------|------:|-------------|
| **Trading** | 12 | Signal bots, DCA, arbitrage, pum

*[truncated — see source for full prompt]*