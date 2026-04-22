# Mcp Servers

> CycoD supports the Model Context Protocol (MCP) for integrating with external tools and services.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Using MCP (Model Context Protocol) Servers with CycoD

CycoD supports the Model Context Protocol (MCP) for integrating with external tools and services. This document explains how to configure and use MCP servers with CycoD.

## What is MCP?

The Model Context Protocol (MCP) is an open protocol that standardizes how applications provide context to Large Language Models (LLMs). It enables secure integration between LLMs and various data sources and tools.

Some examples of what you can do with MCP:
- Connect to databases and query data
- Call APIs and web services
- Execute custom code or tools
- Access external knowledge bases

## Configuring MCP Servers

You can configure MCP servers using the `cycod mcp` commands:

```bash
# List all configured MCP servers
cycod mcp list

# Add a new stdio-based MCP server
cycod mcp add postgres-db --command "/path/to/postgres-mcp-server --connection-string \"postgres://user:pass@localhost:5432/mydb\""

# Add a new SSE-based MCP server
cycod mcp add rest-api --url https://example.com/mcp-sse-endpoint

# Add environment variables to an MCP server
cycod mcp add weather-api --command /path/to/weather-tool --env API_KEY=abc123 --env CACHE_DIR=/tmp

# Get details of a specific MCP server
cycod mcp get postgres-db

# Remove an MCP server
cycod mcp remove postgres-db
```

## How CycoD Uses MCP Servers

When you start a chat session with `--use-mcps`, CycoD automatically:

1. Finds all configured MCP servers
2. Connects to each server
3. Retrieves the list of available tools
4. Makes these tools available to the LLM during the chat

The LLM can then use these tools to perform actions like querying databases, calling APIs, or executing custom code.

## Example Usage

After configuring an MCP server, you can use it in a chat session:

```bash
# Start a chat session
cycod --use-mcps

# Ask a question that might use an MCP tool
User: What is the current weather in New York?

# If a weather MCP tool is configured, the LLM will use it to get 

*[truncated — see source for full prompt]*