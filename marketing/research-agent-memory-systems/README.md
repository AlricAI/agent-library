# Research Agent Memory Systems

> *Research conducted 2026-01-30 by Portal1 subagent*

---

## Table of Contents
1. [Toby Lütke's QMD — Key Ideas](#1-qmd)
2. [Letta (formerly MemGPT) —

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Research Report: Agent Memory & Coordination Systems

*Research conducted 2026-01-30 by Portal1 subagent*

---

## Table of Contents
1. [Toby Lütke's QMD — Key Ideas](#1-qmd)
2. [Letta (formerly MemGPT) — Stateful Agent Memory](#2-letta)
3. [Agent Skills Standard — Progressive Disclosure](#3-agent-skills)
4. [CrewAI Memory — Multi-Agent Shared Memory](#4-crewai)
5. [AutoGen Teams — Multi-Agent Coordination](#5-autogen)
6. [Patterns & Principles Synthesis](#6-synthesis)
7. [Recommendations for Our Setup](#7-recommendations)
8. [Token Efficiency Strategies](#8-token-efficiency)
9. [What to Change in Our Current System](#9-changes)

---

## 1. QMD — Toby Lütke's Local Search Engine for Agent Memory {#1-qmd}

**Repo:** [github.com/tobi/qmd](https://github.com/tobi/qmd) (4.5k stars)
**What it is:** A local CLI search engine for markdown notes, meeting transcripts, documentation, and knowledge bases. Designed to be the memory retrieval layer for agentic workflows.

### Architecture

QMD combines three search strategies into a hybrid pipeline:

1. **BM25 full-text search** (SQLite FTS5) — fast keyword matching
2. **Vector semantic search** (embeddinggemma-300M) — meaning-based similarity
3. **LLM re-ranking** (qwen3-reranker-0.6b) — quality assessment via logprobs

All models run locally via `node-llama-cpp` with GGUF quantized models (~2GB total).

### Key Design Decisions

| Decision | Why It Matters |
|----------|---------------|
| **Hybrid search (BM25 + vector + rerank)** | No single search method works for all queries. BM25 is fast for exact terms, vectors catch semantic meaning, reranking adds judgment. |
| **Reciprocal Rank Fusion (RRF)** | Merges results from multiple search backends without needing to normalize scores to the same scale. |
| **Position-aware blending** | Top-3 results trust retrieval 75%, bottom results trust reranker 60%. Prevents the reranker from displacing exact matches. |
| **Query expansion** (fine-tuned 1.7B model) | Generates alternative

*[truncated — see source for full prompt]*