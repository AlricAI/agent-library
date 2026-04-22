# DEVELOPER WORKFLOW

> Practical workflows for developing across the `crypto-vision` monorepo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Developer Workflow

Practical workflows for developing across the `crypto-vision` monorepo. This covers local setup, daily development, testing, deployment, and troubleshooting.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Environment Variables](#environment-variables)
- [Development Scripts](#development-scripts)
- [Docker Development](#docker-development)
- [App Workflows](#app-workflows)
- [Package Workflows](#package-workflows)
- [Worker & Ingestion Pipelines](#worker--ingestion-pipelines)
- [Database Workflows](#database-workflows)
- [Testing](#testing)
- [Code Quality](#code-quality)
- [Data & Model Pipelines](#data--model-pipelines)
- [Infrastructure](#infrastructure)
- [CI/CD Pipeline](#cicd-pipeline)
- [Pre-Push Checklist](#pre-push-checklist)
- [Secret Hygiene](#secret-hygiene)
- [Debugging Tips](#debugging-tips)
- [Related Documentation](#related-documentation)

---

## Prerequisites

| Requirement  | Version | Notes                                         |
| ------------ | ------- | --------------------------------------------- |
| Node.js      | ≥ 22    | Required — uses ES2022 features               |
| npm          | latest  | Bundled with Node.js                          |
| Docker       | latest  | Optional — for containerized local dev        |
| PostgreSQL   | 16      | Optional — Docker provides it, or use local   |
| Redis        | 7       | Optional — in-memory LRU used when absent     |

### API Keys

Copy the example environment file and fill in your keys:

```bash
cp .env.example .env
```

The server starts without any API keys but will warn about degraded functionality. At minimum, set one AI provider key for AI-powered endpoints.

---

## Quick Start

### Bare-Metal (fastest iteration)

```bash
npm install
npm run dev          # tsx watch on src/index.ts — auto-reloads on file changes
# → http://localhost:8080/health
```

### Using dev.sh (multi-service orchestrator)

```bash
./dev.sh api    

*[truncated — see source for full prompt]*