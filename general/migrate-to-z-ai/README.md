# Migrate To Z Ai

> ## Overview

This guide helps you migrate your ModPorter-AI installation from Ollama/OpenAI backends to Z.AI for better performance and cost efficienc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Migration Guide: Moving to Z.AI Backend

## Overview

This guide helps you migrate your ModPorter-AI installation from Ollama/OpenAI backends to Z.AI for better performance and cost efficiency.

## Quick Migration Steps

### Step 1: Get Your Z.AI API Key

1. Log in to your [Z.AI dashboard](https://z.ai/dashboard)
2. Navigate to API Keys section
3. Create a new API key
4. Copy the key for use in the next step

### Step 2: Configure Repository (for CI/CD)

1. Go to your GitHub repository → Settings → Secrets and variables → Actions
2. Click "New repository secret"
3. Name: `Z_AI_API_KEY`
4. Value: Your Z.AI API key from Step 1
5. Click "Add secret"

### Step 3: Add Repository Variables

In the same section, add these repository variables:

| Variable | Value | Description |
|----------|-------|-------------|
| `Z_AI_MODEL` | `glm-4-plus` | Model to use |
| `Z_AI_BASE_URL` | `https://api.z.ai/v1` | API endpoint |
| `Z_AI_MAX_RETRIES` | `3` | Retry attempts |
| `Z_AI_TIMEOUT` | `300` | Timeout (seconds) |
| `Z_AI_TEMPERATURE` | `0.1` | Sampling temperature |
| `Z_AI_MAX_TOKENS` | `4000` | Max tokens per response |

### Step 4: Test the Migration

Run the migration test script:

```bash
python scripts/test_z_ai_backend.py
```

Or use pytest:

```bash
cd ai-engine
python -m pytest tests/integration/test_z_ai_integration.py -v
```

## Migration Paths

### From OpenAI to Z.AI

**Before:**
```bash
export OPENAI_API_KEY=sk-...
export USE_OPENAI=true
```

**After:**
```bash
export Z_AI_API_KEY=your_z_ai_key
export USE_Z_AI=true
# OpenAI still works as fallback if Z.AI fails
```

### From Ollama to Z.AI

**Before:**
```bash
export USE_OLLAMA=true
export OLLAMA_MODEL=llama3.2
```

**After:**
```bash
export Z_AI_API_KEY=your_z_ai_key
export USE_Z_AI=true
# Ollama still works as fallback if Z.AI fails
```

## Configuration Changes

### Docker Environment

Update your `.env` file:

```env
# Primary: Z.AI
USE_Z_AI=true
Z_AI_API_KEY=your_z_ai_key_here
Z_AI_MODEL=glm-4-plus
Z_AI_BAS

*[truncated — see source for full prompt]*