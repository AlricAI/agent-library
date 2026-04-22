# NATIVE BINARY TRACE LOGGING

> **Complete documentation for the native binary migration with optional trace logging feature**

## Overview

amplihack uses Anthropic's native Claude 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Native Binary Trace Logging

**Complete documentation for the native binary migration with optional trace logging feature**

## Overview

amplihack uses Anthropic's native Claude binary with optional JSONL trace logging. This provides excellent performance, zero external dependencies, and enhanced security.

## What Changed

### Key Improvements

- **No NPM dependency**: Uses native Claude binary directly
- **Optional by default**: Trace logging disabled by default, zero overhead when off
- **High performance**: <0.1ms overhead when disabled, <10ms when enabled
- **Automatic security**: TokenSanitizer removes API keys and secrets automatically
- **Session-scoped logs**: JSONL files organized by session in `.claude/runtime/amplihack-traces/`
- **Direct API integration**: Automatic request/response capture via callbacks

### Performance

| Metric              | Native Binary |
| ------------------- | ------------- |
| Overhead (disabled) | <0.1ms        |
| Overhead (enabled)  | <10ms         |
| NPM dependency      | None          |
| Default state       | Disabled      |
| Security            | Automatic     |

## Quick Start

### Enable Trace Logging

Trace logging is **disabled by default**. Enable it when needed:

```bash
# Enable for single session
AMPLIHACK_TRACE_LOGGING=true amplihack

# Enable permanently
export AMPLIHACK_TRACE_LOGGING=true
echo 'export AMPLIHACK_TRACE_LOGGING=true' >> ~/.bashrc

# Launch amplihack
amplihack
```

### View Traces

```bash
# List trace files
ls -lh .claude/runtime/amplihack-traces/

# View latest trace
tail -f .claude/runtime/amplihack-traces/trace_*.jsonl | jq .

# Analyze token usage
cat .claude/runtime/amplihack-traces/*.jsonl | \
  jq -s '[.[] | select(.response.usage != null) | .response.usage] |
         {calls: length, total_tokens: map(.total_tokens) | add}'
```

## Documentation

### For Users

Start here to learn how to use trace logging:

1. **[Feature Overview](features/trace-logging.md)**
   - What is trace loggi

*[truncated — see source for full prompt]*