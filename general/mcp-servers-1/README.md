# Mcp Servers

> How to set up and use the 6 Model Context Protocol servers — the core technology that connects AI to blockchains.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP Servers Guide

How to set up and use the 6 Model Context Protocol servers — the core technology that connects AI to blockchains.

> **New to MCP?** Don't worry — this guide explains everything from scratch. Also see the [Glossary](GLOSSARY.md) for term definitions.

---

## What Is MCP?

**Model Context Protocol (MCP)** is an open standard (created by Anthropic) that lets AI assistants connect to external tools and data sources.

**The simplest way to understand MCP:** Without MCP, AI can only *talk about* crypto. With MCP, AI can *interact with* crypto.

| Without MCP | With MCP |
|------------|---------|
| "BNB is probably around $600" | "BNB is exactly $623.47 right now" |
| "You could try swapping on PancakeSwap" | *Actually executes the swap for you* |
| "I can't check your wallet" | "Your wallet has 1.5 BNB and 4 tokens" |

Think of MCP like **USB for AI** — a universal way to plug in new capabilities. Each MCP server exposes "tools" (individual actions the AI can call), and any MCP-compatible AI client can use them.

### How MCP Works (Simplified)

```
 You ask Claude a question
        │
        ▼
 Claude recognizes it needs real data
        │
        ▼
 Claude calls an MCP tool (e.g., "get_balance")
        │
        ▼
 The MCP server handles the request
   (talks to the blockchain, exchange, or API)
        │
        ▼
 Server returns the data to Claude
        │
        ▼
 Claude uses the data to answer you in plain English
```

This all happens in about 1-2 seconds, completely automatically.

### Which AI Assistants Support MCP?

| Assistant | MCP Support | Notes |
|-----------|:-----------:|-------|
| Claude Desktop | ✅ | First-class support |
| Claude Code | ✅ | CLI-based |
| GitHub Copilot | ✅ | Via extensions |
| Cursor | ✅ | Built-in |
| Windsurf | ✅ | Built-in |
| ChatGPT | ❌ | Not yet — use as API with wrapper |
| Any MCP client | ✅ | The protocol is open standard |

---

## Quick Setup

All MCP servers follow the same pattern:

```bash
# 1

*[truncated — see source for full prompt]*