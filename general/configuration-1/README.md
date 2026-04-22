# CONFIGURATION

> Complete configuration reference for CloudCurio framework.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration Guide

Complete configuration reference for CloudCurio framework.

## Table of Contents

- [Overview](#overview)
- [Environment Variables](#environment-variables)
- [Configuration Files](#configuration-files)
- [Model Configuration](#model-configuration)
- [Runtime Configuration](#runtime-configuration)
- [Tool Configuration](#tool-configuration)

## Overview

CloudCurio uses a layered configuration system:

1. **Environment Variables**: System-level configuration
2. **Config Files**: Repository-level settings
3. **Agent Specs**: Agent-specific configuration
4. **Runtime Overrides**: Command-line overrides

### Configuration Priority

```
CLI Args > Agent Spec > Config Files > Environment Variables > Defaults
  (highest priority)                                     (lowest priority)
```

## Environment Variables

### Model Provider API Keys

```bash
# OpenAI
export OPENAI_API_KEY="sk-..."
export OPENAI_ORG_ID="org-..."  # Optional

# Anthropic
export ANTHROPIC_API_KEY="sk-ant-..."

# OpenRouter
export OPENROUTER_API_KEY="sk-or-..."

# Google AI
export GOOGLE_API_KEY="..."

# Mistral
export MISTRAL_API_KEY="..."
```

### Ollama Configuration

```bash
# Ollama base URL
export OLLAMA_BASE_URL="http://localhost:11434"

# Default model
export OLLAMA_DEFAULT_MODEL="qwen2.5-coder"
```

### Framework Configuration

```bash
# CrewAI
export CREWAI_VERBOSE="true"
export CREWAI_ALLOW_DELEGATION="false"

# LangChain
export LANGCHAIN_TRACING_V2="true"
export LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
export LANGCHAIN_API_KEY="..."
export LANGCHAIN_PROJECT="cloudcurio"

# PydanticAI
export PYDANTIC_AI_LOG_LEVEL="INFO"
```

### Observability

```bash
# OpenTelemetry
export OTEL_EXPORTER_OTLP_ENDPOINT="http://localhost:4317"
export OTEL_SERVICE_NAME="cloudcurio-agents"
export OTEL_LOG_LEVEL="info"

# Prometheus
export PROMETHEUS_PORT="9090"
export PROMETHEUS_SCRAPE_INTERVAL="15s"

# Jaeger
export JAEGER_AGENT_HOST="localhost"
export JAEGER_AGENT_PORT="6831"

*[truncated — see source for full prompt]*