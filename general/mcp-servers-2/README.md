# MCP SERVERS

> Integration guide for Model Context Protocol servers in CloudCurio.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Model Context Protocol (MCP) Servers Guide

Integration guide for Model Context Protocol servers in CloudCurio.

## Table of Contents

- [Overview](#overview)
- [Available MCP Servers](#available-mcp-servers)
- [Configuration](#configuration)
- [Usage](#usage)
- [Custom MCP Servers](#custom-mcp-servers)

## Overview

Model Context Protocol (MCP) provides standardized interfaces for AI tools and integrations. CloudCurio includes MCP servers for automation and media processing.

### MCP Architecture

```
Agent → MCP Client → MCP Server → Tools/Resources
  ↓         ↓            ↓              ↓
 Spec   Protocol    Standard API   Implementation
```

## Available MCP Servers

### Automation Server

**Location**: `mcp-servers/automation/`

Provides automation tools:
- File operations
- Process management
- System commands
- Scheduling

**Tools:**
- `execute_command` - Run system commands
- `schedule_task` - Schedule automated tasks
- `file_watch` - Monitor file changes
- `process_monitor` - Monitor processes

**Usage:**

```yaml
# In agent spec
tools:
  - id: execute_command
    type: mcp
    entrypoint: automation:execute_command
    config:
      timeout: 30
      shell: bash
```

### Media Server

**Location**: `mcp-servers/media/`

Provides media processing tools:
- Audio processing
- Video editing
- Image manipulation
- Format conversion

**Tools:**
- `process_audio` - Audio editing and mixing
- `process_video` - Video editing and effects
- `convert_format` - Media format conversion
- `extract_audio` - Extract audio from video

**Usage:**

```yaml
# In agent spec
tools:
  - id: process_video
    type: mcp
    entrypoint: media:process_video
    config:
      quality: high
      format: mp4
```

## Configuration

### Server Configuration

`mcp-servers/config.json`:

```json
{
  "servers": {
    "automation": {
      "command": "node",
      "args": ["mcp-servers/automation/index.js"],
      "env": {
        "LOG_LEVEL": "info"
      }
    },
    "media": {
      "c

*[truncated — see source for full prompt]*