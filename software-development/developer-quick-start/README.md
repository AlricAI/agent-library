# DEVELOPER QUICK START

> This guide walks you through setting up your own Azure HayMaker development environment and deploying your first orchestrator and workload.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Developer Quick Start Guide

This guide walks you through setting up your own Azure HayMaker development environment and deploying your first orchestrator and workload.

## Prerequisites

Before you begin, ensure you have:

### Required Tools

| Tool | Version | Installation |
|------|---------|--------------|
| **Azure CLI** | 2.50+ | `curl -sL https://aka.ms/InstallAzureCLIDeb \| sudo bash` |
| **GitHub CLI** | 2.0+ | `sudo apt install gh` or [gh releases](https://github.com/cli/cli/releases) |
| **Python** | 3.11+ | System package or pyenv |
| **uv** | Latest | `curl -LsSf https://astral.sh/uv/install.sh \| sh` |
| **Git** | 2.30+ | System package |

### AI Service (Choose One)

You'll need access to an AI service for knowledge worker content generation:

**Option A: Azure AI Foundry (Recommended)**
```bash
# Create Azure AI resource in Azure Portal or CLI
az cognitiveservices account create \
  --name my-ai-service \
  --resource-group my-rg \
  --kind OpenAI \
  --sku S0 \
  --location eastus

# Deploy a model (e.g., gpt-4o)
az cognitiveservices account deployment create \
  --name my-ai-service \
  --resource-group my-rg \
  --deployment-name gpt-4o \
  --model-name gpt-4o \
  --model-version "2024-05-13" \
  --model-format OpenAI
```

**Option B: Anthropic Claude**
- Sign up at [console.anthropic.com](https://console.anthropic.com)
- Create an API key
- Set `ANTHROPIC_API_KEY` in your `.env` file

**Option C: OpenAI Direct**
- Sign up at [platform.openai.com](https://platform.openai.com)
- Create an API key
- Set `OPENAI_API_KEY` in your `.env` file

---

## Step 1: Azure Credentials Setup

### 1.1 Create a Service Principal

Each developer needs their own Service Principal for isolated deployments:

```bash
# Login to Azure
az login

# Set your subscription
az account set --subscription "Your Subscription Name"

# Create a Service Principal with Contributor access
az ad sp create-for-rbac \
  --name "haymaker-dev-$(whoami)" \
  --role Contributor \
  --sco

*[truncated — see source for full prompt]*