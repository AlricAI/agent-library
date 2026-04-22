# Analytics Dashboard Architecture

> ## Overview
Real-time analytics dashboard for monitoring AzureHayMaker orchestrator execution metrics, costs, telemetry volume, and agent health.

## 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Analytics Dashboard Architecture

## Overview
Real-time analytics dashboard for monitoring AzureHayMaker orchestrator execution metrics, costs, telemetry volume, and agent health.

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                    Azure Static Web App                      │
│  ┌───────────────────────────────────────────────────────┐  │
│  │            React Dashboard (TypeScript)                │  │
│  │                                                         │  │
│  │  ┌──────────────┐  ┌──────────────┐                  │  │
│  │  │ Execution    │  │  Cost        │                  │  │
│  │  │ Timeline     │  │  Breakdown   │                  │  │
│  │  └──────────────┘  └──────────────┘                  │  │
│  │                                                         │  │
│  │  ┌──────────────┐  ┌──────────────┐                  │  │
│  │  │ Agent        │  │  Telemetry   │                  │  │
│  │  │ Status       │  │  Volume      │                  │  │
│  │  └──────────────┘  └──────────────┘                  │  │
│  │                                                         │  │
│  │  ┌──────────────────────────────────────────────┐    │  │
│  │  │      Dashboard State (React Context)          │    │  │
│  │  │  - Time range, filters, WebSocket connection │    │  │
│  │  └──────────────────────────────────────────────┘    │  │
│  └───────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                    │                    │
                    │ HTTPS              │ WebSocket (wss://)
                    ▼                    ▼
┌─────────────────────────────────────────────────────────────┐
│              FastAPI Orchestrator Server                     │
│                                                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ GET /metrics │  │ GET          │  │ 

*[truncated — see source for full prompt]*