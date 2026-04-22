# Mcpfile

> Complete reference guide for the GenMCP MCP File format

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP File Format

## 1. Introduction

GenMCP uses **two separate YAML configuration files** to define an MCP server:

1. **MCP File** (`mcpfile.yaml`) - Defines the capabilities (tools, prompts, resources, resource templates) and invocation bases
2. **Server Config File** (`mcpserver.yaml`) - Defines the server runtime configuration (transport protocol, logging, authentication, TLS)

This separation allows you to:
- Share tool definitions across different server configurations
- Version tool definitions and server configuration independently
- Deploy the same tools with different runtime settings (dev, staging, production)

The MCP file uses schema version `0.2.0` and must be provided when running an MCP server with the `genmcp run` command.

> **Migrating from 0.1.0?** If you're upgrading from the single-file format (schema version 0.1.0), see the [Migration Guide](../MIGRATION.md) for step-by-step instructions.

## 2. MCP File

The MCP file defines what capabilities your MCP server provides. It contains tools, prompts, resources, resource templates, and invocation bases.

### 2.1. Top-Level Object

The root of the MCP file has the following structure:

| Field               | Type                        | Description                                                                                                                                                                                                          | Required |
|---------------------|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| `kind`              | string                      | Must be `"MCPToolDefinitions"`.                                                                                                                                                                                     

*[truncated — see source for full prompt]*