# SIEM TELEMETRY EXPORT

> ## Executive Summary

This specification defines the SIEM Telemetry Export Pipeline for Azure HayMaker, enabling real-time and batch export of M365 an

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SIEM Telemetry Export Pipeline - Implementation Specification

## Executive Summary

This specification defines the SIEM Telemetry Export Pipeline for Azure HayMaker, enabling real-time and batch export of M365 and Azure telemetry data to external Security Information and Event Management (SIEM) platforms. This is a **P0-Critical** feature required for red team exercises where benign "hay" telemetry must appear in target SIEMs alongside malicious "needle" activity.

**Status**: Design Phase
**Priority**: P0-Critical
**Target Completion**: 2-3 weeks
**Dependencies**: Knowledge Worker telemetry collection (✓ Complete)

---

## Table of Contents

1. [Architecture Overview](#architecture-overview)
2. [Component Design](#component-design)
3. [Data Flow](#data-flow)
4. [Telemetry Schema](#telemetry-schema)
5. [Connector Specifications](#connector-specifications)
6. [Configuration Model](#configuration-model)
7. [Error Handling & Resilience](#error-handling--resilience)
8. [Performance Considerations](#performance-considerations)
9. [Security](#security)
10. [Testing Strategy](#testing-strategy)
11. [Implementation Plan](#implementation-plan)
12. [API Design](#api-design)

---

## Architecture Overview

### High-Level Design

```mermaid
graph TB
    subgraph "Knowledge Worker Framework"
        A[M365 Operations] -->|emit events| B[Telemetry Collector]
        C[Azure Operations] -->|emit events| B
        B -->|collect| D[Telemetry Buffer]
    end

    subgraph "SIEM Export Pipeline"
        D -->|batch/stream| E[TelemetryExporter]
        E -->|normalize| F[Event Normalizer]
        F -->|route| G[Connector Router]

        G -->|CEF| H1[Azure Sentinel]
        G -->|HEC| H2[Splunk]
        G -->|Syslog| H3[QRadar]
        G -->|JSON| H4[Elastic]

        I[Configuration Manager] -.config.-> E
        J[Retry Manager] -.retry.-> G
        K[Circuit Breaker] -.protect.-> G
    end

    subgraph "External SIEMs"
        H1 -->|DCR| L1[Sentinel Workspace]
        H2 -->|H

*[truncated — see source for full prompt]*