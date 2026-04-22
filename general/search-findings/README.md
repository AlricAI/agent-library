# SEARCH FINDINGS

> ## Summary

Semantic search is implemented end-to-end but has **fundamental quality issues**. The core problem: embeddings are generated from article 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Search Quality — Findings & Future Work

## Summary

Semantic search is implemented end-to-end but has **fundamental quality issues**. The core problem: embeddings are generated from article body text only, without title/summary/tags/topics enrichment, and there is no vector index — every search does a full table scan.

---

## Critical Findings

### 1. Incomplete Embedding Input (biggest quality issue)

**Problem:** Only `readableContent` (cleaned article body) is embedded. The AI-generated title, summary, key points, tags, and topics are NOT included in the embedding input.

**Why this matters:**
- The summary is a distilled version of the article's meaning — it's often a *better* embedding input than the full noisy body
- Tags and topics provide categorical signal the body text may not contain explicitly
- The title is what users remember and search for
- A user searching "react native performance tips" may not find an article whose body discusses the topic but whose title is "Making Your App Faster"

**Where:** `ingest.ts:102` — `generateEmbedding(readableContent)` only

**Fix:** Compose a richer embedding input that includes title + summary + key points + tags + body (truncated). Something like:

```
Title: {title}
Summary: {summary}
Key Points: {keyPoints.join('. ')}
Tags: {tags.join(', ')}
Topics: {topics.join(', ')}

{readableContent (truncated)}
```

This gives the embedding model the full semantic picture. The summary alone might be a better embedding input than 50K chars of article body for many search queries.

**Trade-off:** This means embedding must happen AFTER `analyzeContent` completes (currently they run in parallel). This adds ~1-2s to pipeline latency. Worth it for quality.

### 2. No Vector Index

**Problem:** The `embeddings` table has no HNSW or IVFFlat index. Every `<=>` query is a sequential scan across all rows.

**Impact:**
- 100 entries: ~10ms (fine)
- 1,000 entries: ~100ms (noticeable)
- 10,000 entries: ~1s (slow)
- 100,000 entries: ~1

*[truncated — see source for full prompt]*