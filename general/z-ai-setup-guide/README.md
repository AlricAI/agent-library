# Z Ai Setup Guide

> ## Overview

This guide explains how to set up and configure Z.AI as the primary LLM backend for ModPorter-AI's AI engine. Z.AI provides high-quality 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Z.AI Integration Setup Guide

## Overview

This guide explains how to set up and configure Z.AI as the primary LLM backend for ModPorter-AI's AI engine. Z.AI provides high-quality GLM models with no additional cost for existing Pro plan subscribers.

## Prerequisites

- Active Z.AI Pro plan subscription
- Z.AI API key (available from your Z.AI dashboard)

## Configuration

### 1. Repository Variables

Add the following repository variables (Settings → Secrets and variables → Actions → Variables):

```
Z_AI_MODEL=glm-4-plus
Z_AI_BASE_URL=https://api.z.ai/v1
Z_AI_MAX_RETRIES=3
Z_AI_TIMEOUT=300
Z_AI_TEMPERATURE=0.1
Z_AI_MAX_TOKENS=4000
```

### 2. Repository Secrets

Add the following repository secret (Settings → Secrets and variables → Actions → New repository secret):

```
Z_AI_API_KEY=your_z_ai_api_key_here
```

**Important**: The secret should be named exactly `Z_AI_API_KEY` for the CI/CD pipeline to detect and configure it properly.

### 3. Local Development

For local development, set these environment variables:

```bash
# Enable Z.AI as primary backend
export USE_Z_AI=true

# Z.AI Configuration
export Z_AI_API_KEY=your_api_key_here
export Z_AI_MODEL=glm-4-plus
export Z_AI_BASE_URL=https://api.z.ai/v1

# Optional configuration
export Z_AI_MAX_RETRIES=3
export Z_AI_TIMEOUT=300
export Z_AI_TEMPERATURE=0.1
export Z_AI_MAX_TOKENS=4000

# Disable Ollama fallback (optional)
export USE_OLLAMA=false
```

Or create a `.env` file:

```env
USE_Z_AI=true
Z_AI_API_KEY=your_api_key_here
Z_AI_MODEL=glm-4-plus
Z_AI_BASE_URL=https://api.z.ai/v1
USE_OLLAMA=false
```

## Supported Models

Z.AI supports several GLM models. Recommended models for ModPorter-AI:

- **glm-4-plus** (default): Best balance of performance and quality
- **glm-4**: High-quality model for complex analysis
- **glm-3-turbo**: Fast responses for simple tasks

## Backend Priority System

The AI engine automatically selects the best available backend in this order:

1. **Z.AI** (if `USE_Z_AI=true` and `Z_AI_AP

*[truncated — see source for full prompt]*