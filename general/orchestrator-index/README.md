# ORCHESTRATOR INDEX

> **A SIMPLE orchestrator that WORKS - No Azure Functions, No Durable Functions**

## Quick Navigation

### 🚀 Getting Started
- **[ORCHESTRATOR_QUICKST

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker FastAPI Orchestrator - Complete Documentation Index

**A SIMPLE orchestrator that WORKS - No Azure Functions, No Durable Functions**

## Quick Navigation

### 🚀 Getting Started
- **[ORCHESTRATOR_QUICKSTART.md](ORCHESTRATOR_QUICKSTART.md)** - Get running in 5 minutes
- **[ORCHESTRATOR_SUMMARY.md](ORCHESTRATOR_SUMMARY.md)** - What we built and why

### 📚 Documentation
- **[ORCHESTRATOR_README.md](ORCHESTRATOR_README.md)** - Complete documentation
- **[DEPLOY_ORCHESTRATOR.md](DEPLOY_ORCHESTRATOR.md)** - Azure deployment guide
- **[MIGRATION_GUIDE.md](MIGRATION_GUIDE.md)** - Migrate from Azure Functions

### 💻 Code Files
- **[orchestrator_server.py](orchestrator_server.py)** - Main FastAPI application (350 lines)
- **[Dockerfile.orchestrator](Dockerfile.orchestrator)** - Docker image definition
- **[docker-compose.orchestrator.yml](docker-compose.orchestrator.yml)** - Docker Compose setup
- **[requirements-orchestrator.txt](requirements-orchestrator.txt)** - Python dependencies

### 🔧 Scripts
- **[run_orchestrator.sh](run_orchestrator.sh)** - Quick start script
- **[test_orchestrator.sh](test_orchestrator.sh)** - Test script

### ⚙️ Configuration
- **[.env.orchestrator.example](.env.orchestrator.example)** - Environment template
- **[.github-workflows-orchestrator.yml](.github-workflows-orchestrator.yml)** - CI/CD pipeline

## Documentation by Purpose

### I Want to...

#### Run it Locally
1. Read: [ORCHESTRATOR_QUICKSTART.md](ORCHESTRATOR_QUICKSTART.md) - "Local Testing" section
2. Run: `./run_orchestrator.sh`
3. Test: `./test_orchestrator.sh`

#### Deploy to Azure
1. Read: [DEPLOY_ORCHESTRATOR.md](DEPLOY_ORCHESTRATOR.md)
2. Build: `az acr build ...`
3. Deploy: `az containerapp create ...`

#### Understand the Architecture
1. Read: [ORCHESTRATOR_SUMMARY.md](ORCHESTRATOR_SUMMARY.md) - "Architecture Comparison" section
2. Read: [ORCHESTRATOR_README.md](ORCHESTRATOR_README.md) - "Architecture Comparison" section
3. Review: [orchestrator_server.py](orc

*[truncated — see source for full prompt]*