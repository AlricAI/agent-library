# DB SYNC SERVER

> **Real-Time Database Replication with Intelligent Query Merging**

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Co

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DB Sync Server - Technical Documentation

**Real-Time Database Replication with Intelligent Query Merging**

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Component Deep Dive](#component-deep-dive)
- [Data Flow Diagrams](#data-flow-diagrams)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Monitoring and Observability](#monitoring-and-observability)
- [Operational Guide](#operational-guide)
- [Failure Modes and Recovery](#failure-modes-and-recovery)
- [Performance Tuning](#performance-tuning)
- [Integration](#integration)
- [Advanced Scenarios](#advanced-scenarios)

## Overview

The DB Sync Server module provides enterprise-grade database replication for Remembrances-MCP. It maintains real-time synchronized copies of the primary SurrealDB instance across multiple secondary databases while providing intelligent query merging capabilities.

### Key Features

- **Asynchronous Replication**: Non-blocking writes with background sync
- **Multi-Database Support**: Sync to multiple secondaries with priorities
- **Intelligent Merging**: Automatic result merging with configurable strategies
- **High Availability**: Graceful degradation and automatic failover
- **Production Ready**: Battle-tested with comprehensive test coverage

### Use Cases

1. **Disaster Recovery**: Maintain hot standby databases for failover
2. **Geographic Distribution**: Replicate data to multiple regions
3. **Load Distribution**: Distribute read queries across replicas
4. **Compliance**: Meet data residency requirements
5. **Analytics**: Dedicated replica for reporting without impacting primary

## Architecture

### System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        Application Layer                            │
│                  (Standard storage.FullStorage API)                 │
└───────────────────────────────┬─────────────────────────────────────┘
                           

*[truncated — see source for full prompt]*