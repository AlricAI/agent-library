# 24 Ml Training Inference

> ## Context

You are working on the machine learning pipeline for crypto-vision. The project has ML components in multiple locations:

### ML Infrastru

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 24 — ML Training & Inference Pipeline

## Context

You are working on the machine learning pipeline for crypto-vision. The project has ML components in multiple locations:

### ML Infrastructure

1. **Training scripts** (`scripts/training/`):
   - `generate-training-data.ts` — Generate training data from BigQuery/API
   - `finetune-gemini.ts` — Fine-tune Gemini models via Vertex AI
   - `eval-models.ts` — Evaluate model performance
   - `validate-data.ts` — Validate training data quality
   - `opensource/` — Open-source model fine-tuning scripts

2. **Inference scripts** (`scripts/inference/`):
   - Runtime inference against trained models

3. **UCAI package** (`packages/ucai/`):
   - Python-based ML package
   - `src/abi_to_mcp/` — ABI to MCP conversion
   - `ucai/` — Core ML module
   - `web/` and `web-v2/` — Web interfaces
   - `pyproject.toml` — Python project config
   - `Makefile` — Build automation
   - Tests in `tests/`

4. **Docker** (`Dockerfile.train`):
   - Training container for GCP Vertex AI

5. **AI route handlers** (`src/routes/`):
   - AI chat, predictions, anomaly detection endpoints
   - Multi-provider: Groq → Gemini → OpenAI → Anthropic → OpenRouter fallback chain

6. **AI library** (`src/lib/ai.ts`):
   - AI provider abstraction
   - Prompt management
   - Response parsing

7. **Existing docs**:
   - `docs/ML_TRAINING.md`
   - `prompts/04-vertex-ai-model-training.md`
   - `prompts/05-open-source-model-finetune.md`

## Task

### 1. Training Data Pipeline (`scripts/training/generate-training-data.ts`)

Complete the training data generator:

```typescript
// Pull data from multiple sources and format for model training:
//
// Data Sources:
//   1. BigQuery — historical price data, market snapshots
//   2. API responses — cached predictions vs actual outcomes
//   3. News corpus — articles with sentiment labels
//   4. Anomaly events — labeled anomalies with resolution
//
// Output Formats:
//   1. JSONL for Gemini fine-tuning (prompt/respo

*[truncated — see source for full prompt]*