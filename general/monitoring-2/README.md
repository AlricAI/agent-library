# MONITORING

> This guide covers monitoring, observability, and alerting for Atlas systems in production environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Monitoring Guide

This guide covers monitoring, observability, and alerting for Atlas systems in production environments.

## Table of Contents

- [Monitoring Overview](#monitoring-overview)
- [System Architecture](#system-architecture)
- [Metrics Collection](#metrics-collection)
- [Logging](#logging)
- [Alerting](#alerting)
- [Dashboard Configuration](#dashboard-configuration)
- [Performance Monitoring](#performance-monitoring)
- [Troubleshooting](#troubleshooting)
- [Best Practices](#best-practices)

## Monitoring Overview

Atlas provides comprehensive monitoring capabilities through multiple integrated components:

- **Real-time monitoring dashboard** for visual system overview
- **Structured logging** for detailed analysis
- **Metrics collection** for performance tracking
- **Alerting system** for proactive issue detection
- **Health checks** for service availability

### Monitoring Components

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Monitoring     │    │  Observability  │    │  Alerting       │
│  Dashboard      │────│  Service        │────│  System         │
│  (Web UI)       │    │  (Metrics/Logs) │    │  (Notifications)│
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
         ┌───────────────────────┼───────────────────────┐
         │                       │                       │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  System         │    │  Application    │    │  Business       │
│  Metrics        │    │  Metrics        │    │  Metrics        │
│  (CPU/Memory)   │    │  (API/Database) │    │  (Processing)   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## System Architecture

### Monitoring Services

1. **Atlas Monitor** (`monitoring_dashboard_service.py`)
   - Web-based dashboard
   - Real

*[truncated — see source for full prompt]*