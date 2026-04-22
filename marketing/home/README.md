# Home

> <p align="center">
  <img src="https://raw.githubusercontent.com/massoudsh/Findash/main/Modules/frontend-nextjs/public/octopus-logo.png" alt="Octopus 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Octopus Trading Platform - Findash

<p align="center">
  <img src="https://raw.githubusercontent.com/massoudsh/Findash/main/Modules/frontend-nextjs/public/octopus-logo.png" alt="Octopus Logo" width="200">
</p>

<p align="center">
  <strong>Advanced AI-Powered Trading Platform with Real-Time Analytics</strong>
</p>

<p align="center">
  <a href="https://www.typescriptlang.org/"><img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"></a>
  <a href="https://nextjs.org/"><img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white" alt="Next.js"></a>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"></a>
  <a href="https://fastapi.tiangolo.com/"><img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI"></a>
  <a href="https://www.postgresql.org/"><img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"></a>
</p>

---

## Overview

The **Octopus Trading Platform (Findash)** is a comprehensive, AI-powered trading system designed for professional traders and institutions. It combines real-time market data, advanced analytics, machine learning models, and automated trading capabilities in a unified, modern interface.

### Platform at a Glance (High-Level Flow)

```mermaid
flowchart LR
    subgraph Users
        U[👤 Trader]
    end
    subgraph Frontend
        D[📊 Dashboard]
        T[💹 Trading]
        P[📈 Portfolio]
    end
    subgraph Backend
        API[🔒 API Gateway]
        FAST[⚡ FastAPI]
        ORCH[🧠 11 AI Agents]
    end
    subgraph Data
        DB[(🗄️ PostgreSQL)]
        REDIS[(⚡ Redis)]
    end
    subgraph External
        MKT[📈 Market Data]
        NEWS[📰 News/Social]
    end
    U --> D & T & P
    D & T &

*[truncated — see source for full prompt]*