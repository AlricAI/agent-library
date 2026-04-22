# Mcpserver

> Complete reference guide for the GenMCP Server Config File format

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GenMCP Server Config File Format

## 1. Introduction

GenMCP uses **two separate YAML configuration files** to define an MCP server:

1. **MCP File** (`mcpfile.yaml`) - Defines the capabilities (tools, prompts, resources, resource templates) and invocation bases
2. **Server Config File** (`mcpserver.yaml`) - Defines the server runtime configuration (transport protocol, logging, authentication, TLS)

This separation allows you to:
- Share tool definitions across different server configurations
- Version tool definitions and server configuration independently
- Deploy the same tools with different runtime settings (dev, staging, production)

The Server Config File uses schema version `0.2.0` and must be provided when running an MCP server with the `genmcp run` command.

> **Migrating from 0.1.0?** If you're upgrading from the single-file format (schema version 0.1.0), see the [Migration Guide](../MIGRATION.md) for step-by-step instructions.

## 2. Server Config File

The Server Config File defines how the MCP server runs, including transport protocol, logging, authentication, and TLS settings.

### 2.1. Top-Level Object

The root of the Server Config File has the following structure:

| Field             | Type            | Description                                                                                                 | Required |
|-------------------|-----------------|-------------------------------------------------------------------------------------------------------------|----------|
| `kind`            | string          | Must be `"MCPServerConfig"`.                                                                                | Yes      |
| `schemaVersion`   | string          | The version of the GenMCP config file format. Must be `"0.2.0"`.                                                      | Yes      |
| `runtime`         | `ServerRuntime` | The runtime settings for the server. If omitted, defaults to `streamablehttp` on port `3000`.         

*[truncated — see source for full prompt]*