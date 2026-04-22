# ARCHITECTURE DIAGRAMS

> ## Table of Contents
1. [High-Level System Overview](#1-high-level-system-overview)
2. [Mid-Level Component Architecture](#2-mid-level-component-archi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Findash Architecture Diagrams

## Table of Contents
1. [High-Level System Overview](#1-high-level-system-overview)
2. [Mid-Level Component Architecture](#2-mid-level-component-architecture)
3. [Low-Level Flow Diagrams](#3-low-level-flow-diagrams)
4. [Data Lineage Diagrams](#4-data-lineage-diagrams)
5. [Class Structure Diagrams](#5-class-structure-diagrams)
6. [Sequence Diagrams](#6-sequence-diagrams)

---

## 1. High-Level System Overview

### 1.1 Complete System Architecture

```mermaid
graph TD
    subgraph "Client Layer"
        WEB[Next.js Frontend]
        MOBILE[Mobile Apps]
        API_CLIENT[API Clients]
    end

    subgraph "Gateway Layer"
        NGINX[NGINX/Traefik]
        CORS[CORS Middleware]
        AUTH[JWT Authentication]
        RATE[Rate Limiter]
    end

    subgraph "Application Layer"
        FASTAPI[FastAPI Application]
        WS[WebSocket Manager]
        CELERY[Celery Workers]
    end

    subgraph "Service Layer"
        MARKET[Market Data Service]
        TRADING[Trading Service]
        PORTFOLIO[Portfolio Service]
        RISK[Risk Service]
        AI[Intelligence Orchestrator]
    end

    subgraph "Data Layer"
        PG[(PostgreSQL/TimescaleDB)]
        REDIS[(Redis Cache)]
        PUBSUB[Redis Pub/Sub]
    end

    subgraph "External Services"
        YAHOO[Yahoo Finance]
        ALPHA[Alpha Vantage]
        NEWS[News APIs]
    end

    WEB --> NGINX
    MOBILE --> NGINX
    API_CLIENT --> NGINX
    
    NGINX --> CORS --> AUTH --> RATE --> FASTAPI
    FASTAPI --> WS
    FASTAPI --> CELERY
    
    FASTAPI --> MARKET
    FASTAPI --> TRADING
    FASTAPI --> PORTFOLIO
    FASTAPI --> RISK
    FASTAPI --> AI
    
    MARKET --> REDIS
    MARKET --> PG
    MARKET --> YAHOO
    MARKET --> ALPHA
    
    TRADING --> REDIS
    TRADING --> PG
    
    PORTFOLIO --> REDIS
    PORTFOLIO --> PG
    
    RISK --> PG
    
    AI --> REDIS
    AI --> PG
    
    WS --> PUBSUB
    PUBSUB --> REDIS

    classDef client fill:#e1f5fe
    classDef 

*[truncated — see source for full prompt]*