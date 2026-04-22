# Mcp

> **Connect AI assistants to your Elasticsearch data.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP Integration

**Connect AI assistants to your Elasticsearch data.** Skills become tools that any MCP-compatible AI can use.

---

## What is MCP?

The [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is an open standard for AI assistants to discover and use tools. Moltler exposes all installed skills as MCP tools, allowing AI agents to:

- **Discover skills** - List available operations with descriptions
- **Understand parameters** - Get input schemas with validation
- **Call skills** - Execute skills and receive structured results

---

## Quick Start

### 1. List Available Tools

```bash
curl -u elastic-admin:elastic-password http://localhost:9200/_escript/mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "method": "tools/list", "id": 1}'
```

Response:
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "tools": [
      {
        "name": "get_recent_errors",
        "description": "Get recent ERROR level logs from the specified index pattern",
        "inputSchema": {
          "type": "object",
          "properties": {
            "index_pattern": {"type": "string", "default": "logs-*"},
            "limit": {"type": "integer", "default": 20}
          }
        }
      }
    ]
  }
}
```

### 2. Call a Tool

```bash
curl -u elastic-admin:elastic-password http://localhost:9200/_escript/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "tools/call",
    "params": {
      "name": "get_recent_errors",
      "arguments": {"limit": 5}
    },
    "id": 1
  }'
```

Response:
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "content": [
      {
        "type": "text",
        "text": "[{\"level\": \"ERROR\", \"service\": \"api\", \"message\": \"Connection timeout\"}]"
      }
    ]
  }
}
```

---

## MCP Protocol Support

| Method | Supported | Description |
|--------|-----------|-------------|
| `initialize` | ✅ | Handshake and capability exchange |
| `tools/list` | ✅ | L

*[truncated — see source for full prompt]*