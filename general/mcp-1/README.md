# MCP

> A.R.E.S includes a full MCP server implementation that exposes tools via the Model Context Protocol, enabling integration with AI assistants like Claude Desktop, Zed, and other MCP-compatible clients.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP (Model Context Protocol) Server

A.R.E.S includes a full MCP server implementation that exposes tools via the Model Context Protocol, enabling integration with AI assistants like Claude Desktop, Zed, and other MCP-compatible clients.

## Features

- **Calculator Tool**: Perform basic arithmetic operations (add, subtract, multiply, divide)
- **Web Search Tool**: Search the web using DuckDuckGo via [daedra](https://github.com/dirmacs/daedra) (no API key required)
- **Server Stats Tool**: Get server statistics and operation counts
- **Echo Tool**: Simple echo for testing connectivity

## Enabling MCP

MCP support is feature-gated. Enable it during compilation:

```bash
cargo build --features mcp
```

Or with other features:

```bash
cargo build --features "mcp,ollama"
```

## Starting the MCP Server

The MCP server runs over stdio (standard input/output) as per the MCP specification:

```rust
use ares::mcp::McpServer;

#[tokio::main]
async fn main() -> anyhow::Result<()> {
    McpServer::start().await?;
    Ok(())
}
```

## Configuring with Claude Desktop

Add the following to your Claude Desktop configuration file:

**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`  
**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "ares": {
      "command": "/path/to/ares-mcp-server",
      "args": []
    }
  }
}
```

## Available Tools

### calculator

Perform basic arithmetic operations.

**Parameters:**
- `operation` (string, required): One of "add", "subtract", "multiply", "divide"
- `a` (number, required): First operand
- `b` (number, required): Second operand

**Example:**
```json
{
  "operation": "multiply",
  "a": 6,
  "b": 7
}
```

**Response:**
```json
{
  "operation": "multiply",
  "a": 6,
  "b": 7,
  "result": 42
}
```

### web_search

Search the web for information using DuckDuckGo.

**Parameters:**
- `query` (string, required): The search query
- `max_results` (integer, optional): Maximum result

*[truncated — see source for full prompt]*