# Rag Architecture

> Retrieval-Augmented Generation (RAG) connects LLMs to external knowledge.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RAG Architecture Patterns

Retrieval-Augmented Generation (RAG) connects LLMs to external knowledge. This guide covers production-ready patterns for building, debugging, and scaling RAG pipelines.

---

## Core Pipeline

```
Documents
  ↓
[1] Chunk        — split into retrievable units
  ↓
[2] Embed        — convert to vector representations
  ↓
[3] Index        — store in vector database
  ↓
              [Query]
                ↓
[4] Retrieve     — find top-K candidates
  ↓
[5] Rerank       — score and filter candidates
  ↓
[6] Augment      — inject context into prompt
  ↓
[7] Generate     — LLM produces grounded response
```

---

## Pattern 1: Naive RAG (Baseline)

The simplest working implementation. Use as a baseline before optimizing.

**Flow:** chunk → embed → cosine similarity → top-K → prompt stuffing

**When to use:** prototyping, small corpora (<10K docs), high retrieval tolerance

**Limitations:**

- Fixed chunk size loses semantic coherence
- Single retrieval pass misses paraphrased queries
- No reranking — noisy candidates reach the LLM

```text
Implementation:
- Chunk size: 512 tokens, 10% overlap
- Embedding: text-embedding-3-small (1536 dims)
- Retrieval: cosine similarity, K=5
- Prompt: system context block + user query
```

---

## Pattern 2: Advanced RAG

Adds query expansion, hybrid retrieval, and reranking. Use in production.

**Flow:** query expansion → hybrid retrieval → cross-encoder reranking → prompt with citations

### Query Expansion

Generate 2–3 variants before retrieval to improve recall:

```text
Original: "how do I reset my password"
Expanded:
  - "password reset instructions"
  - "forgot password recovery steps"
  - "change account password"
```

Retrieve for all variants, deduplicate, then rerank the merged pool.

### Hybrid Retrieval (Dense + Sparse)

```text
Dense:  embedding similarity (semantic matching)
Sparse: BM25 keyword matching (exact term matching)
Merge:  RRF (Reciprocal Rank Fusion) — no weights to tune
```

RRF fo

*[truncated — see source for full prompt]*