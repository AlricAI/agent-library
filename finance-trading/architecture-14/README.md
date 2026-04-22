# Architecture

> The Octopus Trading Platform is built on a modern, scalable microservices architecture designed for high-performance financial data processing.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# System Architecture

The Octopus Trading Platform is built on a modern, scalable microservices architecture designed for high-performance financial data processing.

## Architecture Overview

### Layer Diagram (Mermaid)

```mermaid
flowchart TB
    subgraph Client["👤 Client Layer"]
        WEB[Web App - Next.js]
        MOB[Mobile / API Clients]
        WS[WebSocket Client]
    end
    subgraph Gateway["🔒 API Gateway"]
        NGINX[NGINX / Kong]
    end
    subgraph App["⚡ Application Layer"]
        MKT[Market Data API]
        PORT[Portfolio API]
        RISK[Risk API]
        TRADE[Trading API]
        AUTH[Auth Service]
        WS_MGR[WebSocket Manager]
    end
    subgraph Intelligence["🧠 Intelligence Layer"]
        ORCH[Orchestrator]
        M1[M1 Data] 
        M2[M2 Warehouse]
        M3[M3 Realtime]
        M4[M4 Strategy]
        M5[M5 ML]
        M6[M6 Risk]
        M7[M7 Exec]
        M8[M8 Portfolio]
        M9[M9 Compliance]
        M10[M10 Backtest]
        M11[M11 Alt Data]
    end
    subgraph Data["🗄️ Data Layer"]
        PG[(PostgreSQL / TimescaleDB)]
        REDIS[(Redis)]
        KAFKA[Kafka]
    end
    WEB & MOB & WS --> NGINX --> App
    App --> ORCH
    ORCH --> M1 & M2 & M3 & M4 & M5 & M6 & M7 & M8 & M9 & M10 & M11
    M1 & M2 & M3 & M4 & M5 & M6 & M7 & M8 & M9 & M10 & M11 --> PG & REDIS & KAFKA
```

### ASCII Layer Sketch (Reference)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │  Web App    │  │ Mobile App  │  │  API Client │  │  WebSocket  │        │
│  │ (Next.js)   │  │  (React    │  │  (Python/   │  │   Client    │        │
│  │             │  │   Native)   │  │    JS/Go)   │  │             │        │
│  └──────┬──────┘  └──────┬──────┘  └──────┬───

*[truncated — see source for full prompt]*