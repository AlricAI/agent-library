# Example Http Conversion

> Learn how to automatically convert REST APIs into MCP tools using gen-mcp's OpenAPI conversion

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HTTP API Conversion Example

**[📹 Watch the demo video](https://youtu.be/boMyFzpgJoA)** to see this example in action!

> **Note:** This video was recorded before the project was renamed from `automcp` to `gen-mcp`. The functionality remains the same—just replace `automcp` with `genmcp` in commands.

## Overview

This example demonstrates gen-mcp's most powerful feature: **automatic conversion of HTTP REST APIs into MCP tools**. Instead of writing custom MCP server code, you simply point gen-mcp at an OpenAPI specification, and it instantly creates a working MCP server with all endpoints exposed as callable tools.

### What You'll Learn

- How to convert OpenAPI specs to MCP configurations
- Path parameter substitution in URLs (`/features/{id}`)
- Input schema validation for API calls
- Customizing generated configurations
- Using invocation bases for cleaner configs
- Best practices for API-to-MCP conversion

### Prerequisites

- **gen-mcp installed**: See the [Quick Start guide]({{ '/' | relative_url }}#quick-start)
- **Go installed** (for running the example API): Download from [go.dev](https://go.dev)
- **Basic understanding of REST APIs**: HTTP methods, JSON, etc.

## The Example API

This tutorial uses a simple **Feature Request API** that manages product feature requests. It demonstrates common REST API patterns:

- **GET** endpoints for retrieving data
- **POST** endpoints for creating and updating data
- **DELETE** endpoints for removing data
- Path parameters for resource identification
- JSON request/response bodies

### API Endpoints

| Method | Endpoint             | Description                   |
|--------|----------------------|-------------------------------|
| GET    | `/features`          | List all features (summaries) |
| GET    | `/features/top`      | Get most-voted feature        |
| GET    | `/features/{id}`     | Get detailed feature by ID    |
| POST   | `/features`          | Create new feature request    |
| POST   | `/features/vote` 

*[truncated — see source for full prompt]*