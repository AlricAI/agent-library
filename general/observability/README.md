# OBSERVABILITY

> Monitoring, telemetry, and observability for CloudCurio agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Observability Guide

Monitoring, telemetry, and observability for CloudCurio agents.

## Table of Contents

- [Overview](#overview)
- [OpenTelemetry Integration](#opentelemetry-integration)
- [Metrics](#metrics)
- [Distributed Tracing](#distributed-tracing)
- [Logging](#logging)
- [Dashboards](#dashboards)

## Overview

CloudCurio provides comprehensive observability through:

- **Metrics**: Performance and operational metrics via Prometheus
- **Tracing**: Distributed tracing via Jaeger/OpenTelemetry
- **Logging**: Structured logging with context
- **Dashboards**: Pre-built Grafana dashboards

### Architecture

```
Agent → OpenTelemetry SDK → OTLP Exporter → Collector
  ↓           ↓                   ↓              ↓
Spans     Metrics              HTTP/gRPC    Prometheus
Logs      Events               Protocol      Jaeger
                                             Grafana
```

## OpenTelemetry Integration

### Setup

```python
from cbw_foundry.observability.otel import setup_observability

# Initialize observability
setup_observability(
    service_name="cloudcurio-agents",
    endpoint="http://localhost:4317"
)
```

### Configuration

```python
import os
from opentelemetry import trace, metrics
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.metrics import MeterProvider
from opentelemetry.exporter.otlp.proto.grpc.trace_exporter import OTLPSpanExporter
from opentelemetry.exporter.otlp.proto.grpc.metric_exporter import OTLPMetricExporter
from opentelemetry.sdk.resources import Resource


def setup_observability(
    service_name: str = "cloudcurio",
    endpoint: str = None
):
    """Setup OpenTelemetry observability."""
    
    # Get configuration
    endpoint = endpoint or os.getenv("OTEL_EXPORTER_OTLP_ENDPOINT", "http://localhost:4317")
    
    # Create resource
    resource = Resource.create({
        "service.name": service_name,
        "service.version": "0.4.0",
        "deployment.environment": os.getenv("ENVIRONMENT", "devel

*[truncated — see source for full prompt]*