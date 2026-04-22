# DOCKER DEPLOYMENT

> Container deployment guide for CloudCurio framework.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Docker Deployment Guide

Container deployment guide for CloudCurio framework.

## Table of Contents

- [Overview](#overview)
- [Docker Setup](#docker-setup)
- [Observability Stack](#observability-stack)
- [Production Deployment](#production-deployment)
- [Best Practices](#best-practices)

## Overview

CloudCurio provides Docker configurations for:
- Observability stack (Prometheus, Grafana, Jaeger)
- Agent runtime containers
- Development environments
- Production deployments

## Docker Setup

### Prerequisites

```bash
# Install Docker
curl -fsSL https://get.docker.com | sh

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# Verify installation
docker --version
docker-compose --version
```

### Project Structure

```
docker/
├── compose/
│   ├── observability/
│   │   ├── docker-compose.yml
│   │   ├── prometheus/
│   │   │   └── prometheus.yml
│   │   └── grafana/
│   │       └── dashboards/
│   └── agents/
│       └── docker-compose.yml
└── Dockerfile
```

## Observability Stack

### Starting the Stack

```bash
cd docker/compose/observability
docker-compose up -d
```

Services available:
- **Prometheus**: http://localhost:9090 - Metrics collection
- **Grafana**: http://localhost:3000 - Visualization (admin/admin)
- **Jaeger**: http://localhost:16686 - Distributed tracing

### Docker Compose Configuration

`docker/compose/observability/docker-compose.yml`:

```yaml
version: '3.8'

services:
  prometheus:
    image: prom/prometheus:latest
    container_name: cloudcurio-prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.path=/prometheus'
    restart: unless-stopped
    networks:
      - cloudcurio

  graf

*[truncated — see source for full prompt]*