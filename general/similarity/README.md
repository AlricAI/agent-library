# SIMILARITY

> How floop detects and merges duplicate behaviors.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Similarity Pipeline

How floop detects and merges duplicate behaviors.

## Overview

When `floop deduplicate` (or the `floop_deduplicate` MCP tool) runs, it compares every pair of behaviors in the store to find duplicates. Similarity is computed using a **3-tier fallback chain** — the first method that produces a result wins:

1. **Embedding similarity** — cosine similarity between vector embeddings
2. **LLM comparison** — structured semantic comparison via a language model
3. **Jaccard word overlap** — rule-based word overlap (always available)

Pairs that meet the similarity threshold are flagged as duplicates and optionally merged.

## Embedding Similarity

When an LLM client implements the `EmbeddingComparer` interface, floop generates embeddings for each behavior's content and computes **cosine similarity** between the resulting vectors.

- Range: -1.0 to 1.0 (in practice, 0.0 to 1.0 for normalized text embeddings)
- Vectors are L2-normalized before comparison
- Returns 0.0 for zero-magnitude or mismatched-length vectors

The **local provider** (`llm.provider = local`) runs offline embedding via GGUF models loaded through yzma (purego bindings to llama.cpp). It uses nomic-embed-text-v1.5 (Q4_K_M) to generate 768-dimension embeddings locally with no API keys or network access required. This is typically the fastest tier in the chain.

Providers that support embeddings: `openai`, `ollama`, `local`.

## LLM Comparison

When embeddings are unavailable (or when the provider does not implement `EmbeddingComparer`), floop falls back to LLM-based comparison via `CompareBehaviors`. The model receives both behaviors and returns a structured result:

- **Semantic similarity** — 0.0 to 1.0 score
- **Intent match** — whether the behaviors target the same underlying intent
- **Merge recommendation** — whether the model recommends merging

The comparison uses `llm.comparison_model` (configurable). This is slower than embedding similarity but can capture nuanced semantic rel

*[truncated — see source for full prompt]*