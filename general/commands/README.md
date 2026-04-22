# Commands

> Complete reference for all gen-mcp CLI commands

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Command Reference

The `genmcp` CLI provides commands for managing MCP servers, converting API specifications, and building container images. This guide covers all available commands with detailed explanations and examples.

---

## Quick Reference

| Command               | Description             | Common Usage                                                        |
|-----------------------|-------------------------|---------------------------------------------------------------------|
| [`run`](#run)         | Start an MCP server     | `genmcp run -f mcpfile.yaml -s mcpserver.yaml`                      |
| [`stop`](#stop)       | Stop a running server   | `genmcp stop -f mcpfile.yaml`                                       |
| [`inspect`](#inspect) | Show server details     | `genmcp inspect -s mcpserver.yaml`                                  |
| [`convert`](#convert) | Convert OpenAPI to MCP  | `genmcp convert openapi.json`                                       |
| [`build`](#build)     | Build container image   | `genmcp build -f mcpfile.yaml -s mcpserver.yaml --tag myapi:latest` |
| [`version`](#version) | Display version info    | `genmcp version`                                                    |

---

## <span style="color: #E6622A;">run</span>

Start an MCP server from GenMCP config files.

#### Usage

```bash
genmcp run [flags]
```

#### Flags

| Flag              | Short | Default          | Description                                      |
|-------------------|-------|------------------|--------------------------------------------------|
| `--file`          | `-f`  | `mcpfile.yaml`   | Path to the MCP File (MCPToolDefinitions)        |
| `--server-config` | `-s`  | `mcpserver.yaml` | Path to the server config file (MCPServerConfig) |
| `--detach`        | `-d`  | `false`          | Run server in background (detached mode)         |

#### How It Works

The `run` command:

1. **Validates both files** - Checks syntax and schema validity of both the MC

*[truncated — see source for full prompt]*