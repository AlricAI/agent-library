# Health Checks

> This document describes the health check endpoints implemented in the ModPorter AI backend for Kubernetes readiness and liveness probes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Health Check Endpoints

This document describes the health check endpoints implemented in the ModPorter AI backend for Kubernetes readiness and liveness probes.

## Overview

The backend provides three health check endpoints:

| Endpoint | Purpose | Use Case |
|----------|---------|-----------|
| `/health` | Basic health check | Simple uptime verification |
| `/health/liveness` | Liveness probe | Kubernetes liveness check |
| `/health/readiness` | Readiness probe | Kubernetes readiness check |

## Endpoints

### 1. Basic Health Check

**Endpoint:** `GET /health`

Returns a basic health status indicating the application is running.

**Response:**
```json
{
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00.000000",
  "checks": {
    "application": {
      "status": "running",
      "message": "Application process is running"
    }
  }
}
```

### 2. Liveness Probe

**Endpoint:** `GET /health/liveness`

Checks if the application is running and doesn't need to be restarted. This endpoint does NOT check dependencies to avoid restart loops.

**Response:**
```json
{
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00.000000",
  "checks": {
    "application": {
      "status": "running",
      "message": "Application process is running"
    }
  }
}
```

**Use in Kubernetes:**
```yaml
livenessProbe:
  httpGet:
    path: /health/liveness
    port: 8000
  initialDelaySeconds: 30
  periodSeconds: 10
```

### 3. Readiness Probe

**Endpoint:** `GET /health/readiness`

Checks if the application can serve traffic by verifying all required dependencies are available:
- Database connectivity
- Redis connectivity (optional - results in degraded status if unavailable)

**Response (all healthy):**
```json
{
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00.000000",
  "checks": {
    "dependencies": {
      "database": {
        "status": "healthy",
        "latency_ms": 5.2,
        "message": "Database connection successful"
      },
      "redis": {
        "

*[truncated — see source for full prompt]*