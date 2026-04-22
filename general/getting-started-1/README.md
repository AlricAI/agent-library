# Getting Started

> Welcome to ModPorter AI - the first AI-powered tool that converts Minecraft Java Edition mods to Bedrock Edition add-ons.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started with ModPorter AI

Welcome to ModPorter AI - the first AI-powered tool that converts Minecraft Java Edition mods to Bedrock Edition add-ons.

## What is ModPorter AI?

ModPorter AI automates 60-80% of the work required to convert Java mods to Bedrock add-ons, saving you months of manual rewriting. Our multi-agent AI system:

- Analyzes Java code structure and dependencies
- Translates Java logic to JavaScript (Bedrock Script API)
- Converts textures, models, and sounds
- Validates the conversion for errors
- Packages everything into a ready-to-use .mcaddon file

## Prerequisites

### For Local Development

Before setting up locally, ensure you have:

- **Docker & Docker Compose** (recommended) - handles all dependencies automatically
- **OR** for manual setup:
  - Node.js 22.12+ LTS (for frontend with Vite 7.2.2+)
  - Python 3.9+ (for backend)
  - PostgreSQL 15+ (database)
  - Redis 7+ (caching)

### For Using the Web App

- **A Java mod file** (.jar or .zip) that you want to convert
- **Basic understanding** of Minecraft modding (helpful but not required)
- **A Bedrock testing environment** (Minecraft Bedrock Edition on any platform)

## Installation

### Option 1: Docker (Recommended)

```bash
# Clone the repository
git clone https://github.com/anchapin/ModPorter-AI.git
cd ModPorter-AI

# Copy environment variables
cp .env.example .env
```

Edit `.env` and add your API keys:

```bash
# AI API Keys (required)
OPENAI_API_KEY=your-openai-api-key
ANTHROPIC_API_KEY=your-anthropic-api-key
```

### Option 2: Manual Local Setup

```bash
# Install all dependencies
pnpm run install-all
```

## Quick Start

### Running Locally with Docker

```bash
# Start all services
docker compose up -d

# Check service status
docker compose ps
```

**Service URLs:**
- Frontend: http://localhost:3000
- Backend API: http://localhost:8080
- AI Engine: http://localhost:8001
- PostgreSQL: localhost:5433
- Redis: localhost:6379

### First Conversion

1. **Open the web interfac

*[truncated — see source for full prompt]*