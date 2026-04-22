# SEARCH

> ## Overview

mymemory uses **embedding-based semantic search**. Instead of matching keywords, it compares the *meaning* of your query against the mean

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Semantic Search — How It Works

## Overview

mymemory uses **embedding-based semantic search**. Instead of matching keywords, it compares the *meaning* of your query against the meaning of every entry. This is powered by OpenAI's `text-embedding-3-small` model and PostgreSQL's `pgvector` extension.

---

## How Similarity Is Calculated

```mermaid
flowchart TD
    subgraph Ingestion ["Ingestion (happens once per entry)"]
        A["Raw content scraped\n(Jina Reader / Firecrawl)"] --> B["cleanContent()\nGPT-4o-mini removes\nnav, ads, footers"]
        B --> C["readableContent\n(clean article body)"]
        C --> D["generateEmbedding()\nOpenAI text-embedding-3-small"]
        D --> E["1536-dim vector\nstored in embeddings table"]
    end

    subgraph Search ["Search (happens per query)"]
        F["User types query\ne.g. 'react native performance'"] --> G["generateEmbedding()\nsame model as ingestion"]
        G --> H["Query vector\n1536 dimensions"]
        H --> I["pgvector cosine distance\nquery_vec <=> entry_vec"]
        I --> J["similarity = 1 - distance\n0.0 = unrelated, 1.0 = identical"]
        J --> K["Filter: similarity >= 0.3\nSort: highest first\nReturn top 15"]
    end

    E -.->|"compared against"| I
```

### The Math

**Cosine similarity** measures the angle between two vectors, ignoring magnitude:

```
similarity = 1 - cosine_distance(query_vector, entry_vector)

Where cosine_distance = 1 - (A . B) / (||A|| * ||B||)

Result: 0.0 (completely unrelated) to 1.0 (semantically identical)
```

pgvector's `<=>` operator computes cosine distance. We convert to similarity by subtracting from 1.

---

## What Gets Embedded

This is the critical question — **what text produces the vector determines search quality**.

```mermaid
flowchart LR
    subgraph URL_Entry ["URL Entry"]
        U1["Raw scraped markdown\n(50K+ chars, noisy)"] --> U2["cleanContent()\nAI noise removal"]
        U2 --> U3["readableContent\n(article body only)"]
        U3 --> U4["generat

*[truncated — see source for full prompt]*