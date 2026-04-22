# ENHANCED MODEL SELECTOR GUIDE

> ## 🎯 Overview

The Enhanced Model Selector is a smart, cost-optimized system that automatically selects the best available model for each task, prior

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhanced Model Selector System Guide

## 🎯 Overview

The Enhanced Model Selector is a smart, cost-optimized system that automatically selects the best available model for each task, prioritizing free models while maintaining quality and performance.

## 🏗️ Architecture

### **Free-First Strategy**
- Always tries free models before paid ones
- Intelligent fallback from free → paid within each tier
- Maximizes cost savings while maintaining reliability

### **Tiered Model Selection**
- **Premium Tier**: High-quality models for complex tasks (classification, diarization)
- **Budget Tier**: Fast, cost-effective models for bulk operations (summaries, entities)
- **Fallback Tier**: Balanced models for general use

### **Smart Constraints**
- **Fast Models**: Optimized for speed-sensitive tasks
- **Quality Models**: Optimized for accuracy-critical tasks
- **Balanced Models**: Good all-around performance

## 🔧 Configuration

### **Add to your `config/.env` file:**

```bash
# Paid Model Tiers
MODEL_PREMIUM=google/gemini-2.0-flash-lite-001
MODEL_FALLBACK=google/gemini-2.0-flash-lite-001
MODEL_BUDGET=mistralai/mistral-7b-instruct

# Free Premium Models (for important/complex tasks)
MODEL_FREE_PREMIUM_1=deepseek/deepseek-r1:free
MODEL_FREE_PREMIUM_2=deepseek/deepseek-v3:free
MODEL_FREE_PREMIUM_3=meta-llama/llama-3.1-8b-instruct:free

# Free Fallback Models (balanced performance)
MODEL_FREE_FALLBACK_1=google/gemma-2-9b-it:free
MODEL_FREE_FALLBACK_2=mistralai/mistral-7b-instruct:free
MODEL_FREE_FALLBACK_3=qwen/qwen-2.5-7b-instruct:free

# Free Budget Models (for bulk/cheap tasks)
MODEL_FREE_BUDGET_1=mistralai/mistral-7b-instruct:free
MODEL_FREE_BUDGET_2=qwen/qwen-2.5-7b-instruct:free
MODEL_FREE_BUDGET_3=google/gemma-2-9b-it:free
```

## 🚀 Usage

### **Basic Usage**
```python
from helpers.model_selector import select_model

# Select best model for tier
model = select_model(tier="premium")
model = select_model(tier="budget")
model = select_model(tier="fallback")
```

### **Wi

*[truncated — see source for full prompt]*