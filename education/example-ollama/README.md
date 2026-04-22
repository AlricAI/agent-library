# Example Ollama

> Learn how to connect local language models to AI assistants using gen-mcp with Ollama

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Ollama Integration Example

**[📹 Watch the demo video](https://youtu.be/yqJV9rNwfg8)** to see this example in action!

> **Note:** This video was recorded before the project was renamed from `automcp` to `gen-mcp`. The functionality remains the same—just replace `automcp` with `genmcp` in commands.

## Overview

This example demonstrates how to expose [Ollama](https://ollama.com/), a popular local language model runtime, as MCP tools using gen-mcp. By wrapping Ollama's functionality, you can enable AI assistants to interact with your local language models seamlessly—no custom server code required.

### What You'll Learn

- How to expose HTTP APIs as MCP tools
- How to wrap CLI commands as MCP tools
- The difference between HTTP-based and CLI-based integrations
- Core gen-mcp configuration concepts for tool definitions

### Prerequisites

- **Ollama installed**: Download from [ollama.com](https://ollama.com)
- **gen-mcp installed**: See the [Quick Start guide]({{ '/' | relative_url }}#quick-start)
- **Basic understanding of YAML**: For configuration files

## Two Integration Approaches

gen-mcp supports two different methods for integrating with Ollama, each with its own advantages:

### HTTP-Based Integration (Recommended)

The HTTP approach calls Ollama's REST API directly:

**Advantages:**
- ✅ More reliable with structured JSON responses
- ✅ Better error handling
- ✅ Supports advanced features like streaming control
- ✅ Easier to debug

**Use when:** You want production-grade integration with complete feature access

### CLI-Based Integration

The CLI approach executes `ollama` commands directly:

**Advantages:**
- ✅ Simpler configuration
- ✅ Works without HTTP endpoint
- ✅ Familiar to command-line users

**Use when:** You need quick prototyping or prefer command-line interaction

## HTTP-Based Integration Tutorial

Let's walk through creating an HTTP-based Ollama integration step-by-step.

### Step 1: Start Ollama

Ensure Ollama is running locally:

```bash
ol

*[truncated — see source for full prompt]*