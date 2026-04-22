# Index

> **The skills framework for Elasticsearch.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Moltler

**The skills framework for Elasticsearch.** Build, share, and run skills on your data.

---

## What is Moltler?

Moltler is a **framework for building skills** - reusable operations that run directly on your Elasticsearch data. Create your own skills, share them with the community, and leverage 155+ ready-to-use skills.

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER / AI AGENT                          │
└─────────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        ▼                     ▼                     ▼
┌───────────────┐    ┌───────────────┐    ┌───────────────┐
│  MoltlerHub   │    │  Moltler CLI  │    │  Moltler MCP  │
│  (Web Portal) │    │  (Terminal)   │    │  (AI Bridge)  │
└───────────────┘    └───────────────┘    └───────────────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│               Elasticsearch + elastic-script plugin             │
│                        (Skills Runtime)                         │
└─────────────────────────────────────────────────────────────────┘
```

| Component | Purpose | Required |
|-----------|---------|----------|
| **elastic-script plugin** | Elasticsearch plugin that executes skills | ✅ Yes |
| **Moltler CLI** | Install and manage skills from your terminal | ✅ Yes |
| **MoltlerHub** | Web portal to browse, search, and discover skills | Optional |
| **Moltler MCP** | Bridge for AI agents (Claude, Cursor, etc.) | Optional |

---

## Getting Started

Choose your installation path:

<div class="grid cards" markdown>

-   :material-rocket-launch:{ .lg .middle } **Try It Out**

    Demo, evaluation, or development

    [:octicons-arrow-right-24: Quick Start](#quick-start)

  

*[truncated — see source for full prompt]*