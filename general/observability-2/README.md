# Observability

> Ratatoskr integrates with [OpenTelemetry](https://opentelemetry.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Observability

Ratatoskr integrates with [OpenTelemetry](https://opentelemetry.io/) for distributed tracing and metrics. All instrumentation uses the standard `System.Diagnostics` APIs — `ActivitySource` for tracing and `Meter` for metrics.

## Setup

Register the Ratatoskr activity source and meter with the .NET OpenTelemetry SDK:

[!code-csharp[](../examples/Docs/Program.cs#ConfigureOpenTelemetry)]

The constants `RatatoskrDiagnostics.ActivitySourceName` and `RatatoskrDiagnostics.MeterName` are both `"Ratatoskr"`.

## Tracing

Ratatoskr creates `Activity` spans at key pipeline stages:

- **Publish** — A span is created when `PublishDirectAsync` is called, covering serialization and transport send
- **Consume** — A span is created when a message is received from the transport, covering routing and dispatch
- **Dispatch** — A child span covers handler invocation
- **Outbox/Inbox** — Spans cover background processor batch operations

### W3C Trace Context Propagation

Trace context is automatically propagated through messages:

1. On publish, Ratatoskr stores `traceparent` and `tracestate` in CloudEvents trace fields
2. On consume, Ratatoskr first restores trace context from those CloudEvents fields and falls back to bare transport `traceparent`/`tracestate` headers when needed
3. The restored context is used to create a child activity, continuing the distributed trace across services

This means your existing APM tools (Jaeger, Zipkin, Azure Monitor, Datadog, etc.) will show end-to-end traces spanning publish → transport → consume → handle.

## Metrics Reference

All metrics are emitted on the `"Ratatoskr"` meter.

### Standard OpenTelemetry Messaging Metrics

| Metric | Type | Unit | Description |
|--------|------|------|-------------|
| `messaging.client.operation.duration` | Histogram | `s` | Duration of messaging operation initiated by a producer or consumer client |
| `messaging.client.sent.messages` | Counter | `{message}` | Number of messages producer attem

*[truncated — see source for full prompt]*