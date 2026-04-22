# README

> > **42 production-ready AI agent definitions for DeFi, portfolio management, trading, and Web3 workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🤖 DeFi Agents API - AI Agent Definitions for Web3 
 
> **42 production-ready AI agent definitions for DeFi, portfolio management, trading, and Web3 workflows. RESTful JSON API with 30+ language support.**

A comprehensive, discoverable API hosting specialized AI agent schemas with universal compatibility. Works with any AI platform, LLM, or chatbot that supports agent indexes - no vendor lock-in, no platform restrictions. Perfect for developers, LLMs, and AI systems building Web3 applications.

---

## ✨ Key Features

- ✅ **42 Production-Ready Agents** - DeFi, portfolio, trading, Web3, education
- ✅ **18 Languages** - Automated i18n translation workflow ([Learn More →](./docs/I18N_WORKFLOW.md))
- ✅ **RESTful JSON API** - Easy integration for developers and LLMs ([API Docs →](./docs/API.md))
- ✅ **Machine-Readable Indexes** - Agent manifest for AI crawlers ([agents-manifest.json](./agents-manifest.json))
- ✅ **Universal Format** - Standard JSON schema works with any platform
- ✅ **No Vendor Lock-in** - Switch platforms without losing work
- ✅ **Open Source** - MIT licensed, fully transparent 
- ✅ **SEO & AI Friendly** - robots.txt, structured data, semantic indexing
- ✅ **CDN Hosted** - GitHub Pages for fast global access
- ✅ **Custom Domain Ready** - Easy white-labeling

---

## 🚀 Quick Start

### For AI Systems & LLMs

Discover agents via the API:

```bash
# Get all agents (English)
curl https://sperax.click/index.json

# Get agents in any language
curl https://sperax.click/index.zh-CN.json

# Get agent manifest for indexing
curl https://sperax.click/agents-manifest.json
```

[Complete API Documentation →](./docs/API.md)

### For Users

Add agents to your AI platform:

```
https://sperax.click/index.json
```

Or with language:

```
https://sperax.click/index.{locale}.json
```

### For Developers

```bash
git clone https://github.com/nirholas/defi-agents.git
cd defi-agents
bun install
bun run format
bun run build
```

[Complete Development Workflow Guide →](./do

*[truncated — see source for full prompt]*