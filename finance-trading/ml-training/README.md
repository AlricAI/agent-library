# ML TRAINING

> > Fine-tuning crypto-specialized LLMs with Vertex AI (Gemini) and open-source models (Llama, Mistral, Qwen).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ML Training Pipeline

> Fine-tuning crypto-specialized LLMs with Vertex AI (Gemini) and open-source models (Llama, Mistral, Qwen).

## Overview

Crypto Vision trains domain-specific language models for cryptocurrency analysis. The pipeline generates training data from live API endpoints, validates it, and fine-tunes models through two paths:

1. **Vertex AI (Gemini)** — managed fine-tuning on GCP with Gemini 2.0 Flash
2. **Open-Source (Llama/Mistral/Qwen)** — QLoRA fine-tuning with Unsloth on GPU nodes

```
Live Market APIs  →  Training Data Generator  →  Validation  →  Fine-Tuning
                                                                    │
                                                    ┌───────────────┼───────────────┐
                                                    │               │               │
                                              Vertex AI         Local GPU       GKE GPU
                                              (Gemini)          (Unsloth)       (K8s Job)
                                                    │               │               │
                                                    └───────────────┼───────────────┘
                                                                    │
                                                              Inference
                                                    ┌───────────────┼───────────────┐
                                                    │               │               │
                                              Vertex AI         vLLM            K8s Inference
                                              Endpoint          Server          Deployment
```

## Quick Start

```bash
# 1. Generate training data from live APIs
npm run training:generate

# 2. Validate the JSONL output
npm run training:validate

# 3a. Fine-tune on Vertex AI (Gemini)
npm run training:finetune

# 3b. Prepare for open-source training
npm run training:prepare

# 3b. Train locally with QLoRA


*[truncated — see source for full prompt]*