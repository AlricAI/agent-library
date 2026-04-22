# RAG INTEGRATION

> ## Overview

The ARES RAG (Retrieval-Augmented Generation) pipeline provides semantic search and context injection capabilities for document-based kno

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ARES RAG Pipeline Integration

## Overview

The ARES RAG (Retrieval-Augmented Generation) pipeline provides semantic search and context injection capabilities for document-based knowledge bases. This document describes the integration points, usage patterns, and implementation details.

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     Document Ingestion Flow                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. Document Upload                                              │
│     └─> POST /api/rag/ingest                                     │
│                                                                  │
│  2. Chunking                                                     │
│     ├─> Word Chunking (200 words, 50 overlap)                   │
│     ├─> Semantic Chunking (500 words, structure-aware)          │
│     └─> Character Chunking (500 chars, 100 overlap)             │
│                                                                  │
│  3. Embedding Generation                                         │
│     └─> Local ONNX models (fastembed)                           │
│         ├─> BAAI/bge-small-en-v1.5 (default, 384 dims)          │
│         ├─> BAAI/bge-base-en-v1.5 (768 dims)                    │
│         └─> 30+ other models supported                          │
│                                                                  │
│  4. Vector Storage                                               │
│     └─> AresVector (HNSW, pure Rust)                            │
│         ├─> Cosine similarity metric                            │
│         ├─> Persistent or in-memory mode                        │
│         └─> User-scoped collections                             │
│                                                                  │
└─────────────────────────────────────────────

*[truncated — see source for full prompt]*