# Speech Setup

> This guide explains how to set up and use speech recognition in cycod.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Speech Recognition Setup Guide

This guide explains how to set up and use speech recognition in cycod.

## Overview

cycod supports speech-to-text input using Azure Cognitive Services Speech SDK. This allows you to speak your prompts instead of typing them in interactive chat mode.

## Prerequisites

- Azure subscription (free tier available)
- Microphone hardware
- Internet connection

## Azure Speech Service Setup

### 1. Create Azure Speech Resource

1. Go to the [Azure Portal](https://portal.azure.com)
2. Click "Create a resource"
3. Search for "Speech"
4. Select "Speech" (Cognitive Services)
5. Click "Create"
6. Fill in the required fields:
   - **Subscription**: Select your Azure subscription
   - **Resource group**: Create new or use existing
   - **Region**: Select a region close to you (e.g., `westus2`, `eastus`, `westeurope`)
   - **Name**: Choose a unique name for your resource
   - **Pricing tier**: Select Free (F0) for testing, or Standard (S0) for production
7. Click "Review + create", then "Create"

### 2. Get Your Credentials

After the resource is created:

1. Go to your Speech resource in the Azure Portal
2. Click "Keys and Endpoint" in the left menu
3. You'll see two keys (KEY 1 and KEY 2) and a region
4. Copy **KEY 1** (or KEY 2 - either works)
5. Note your **REGION** (e.g., `westus2`)

## Configure cycod

### Option 1: User-Level Configuration (Recommended)

Store credentials in your user profile so all projects can use them:

```bash
# Create config directory if it doesn't exist
mkdir -p ~/.cycod

# Save your speech key
echo "your-subscription-key-here" > ~/.cycod/speech.key

# Save your region
echo "westus2" > ~/.cycod/speech.region
```

### Option 2: Project-Level Configuration

Store credentials in a specific project:

```bash
# Create config directory in your project
mkdir -p .cycod

# Save your speech key
echo "your-subscription-key-here" > .cycod/speech.key

# Save your region
echo "westus2" > .cycod/speech.region
```

### Option 3: Glo

*[truncated — see source for full prompt]*