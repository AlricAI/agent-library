# Opentelemetry Genai

> Vendor lock-in to observability layers has cost you money.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenTelemetry GenAI Semantic Conventions

Vendor lock-in to observability layers has cost you money. Decoupling telemetry collection from analysis backends lets you migrate from Datadog to Grafana without rewriting instrumentation. OpenTelemetry GenAI Semantic Conventions (GA March 2026) is the standard way forward.

> _Reference: [OpenTelemetry GenAI Specifications](https://opentelemetry.io/docs/specs/semconv/gen-ai/). Implemented by Datadog, Grafana, Uptrace, and OTel Collector as first-class signal types._

## Why this matters

**Problem**: Vendor SDKs tie your instrumentation code to their platform. Switching providers means rewriting every telemetry point. Semantic Conventions decouple what you measure from how you analyze it.

**Solution**: Use standard span attributes (`gen_ai.request.model`, `gen_ai.usage.input_tokens`, etc.) via `opentelemetry-sdk`. Your code stays the same. Export to Datadog, Grafana, Uptrace, or any OTel Collector backend interchangeably.

**Scope**: LLM operations (requests, token usage, tool calls), not application-level metrics. For cost tracking across models, filtering by model/org, and debugging token-efficiency.

## Core span attributes

Standard attributes every LLM span should carry:

| Attribute | Type | Example | Required |
|-----------|------|---------|----------|
| `gen_ai.operation.name` | string | `"completion"`, `"embedding"` | Yes |
| `gen_ai.request.model` | string | `"gpt-4"`, `"claude-3-opus"` | Yes |
| `gen_ai.request.model.architecture` | string | `"transformer"` | No |
| `gen_ai.request.max_tokens` | int | `2048` | No |
| `gen_ai.response.model` | string | `"gpt-4-turbo"` (actual deployed) | No |
| `gen_ai.response.id` | string | `"chatcmpl-8c3i8..."` | No (see pitfalls) |
| `gen_ai.response.finish_reasons` | array | `["length"]`, `["tool_calls"]` | Yes |
| `gen_ai.usage.input_tokens` | int | `142` | Yes |
| `gen_ai.usage.output_tokens` | int | `418` | Yes |
| `gen_ai.usage.cache.creation_input_tokens` | int | `50

*[truncated — see source for full prompt]*