# MEMORY CONTEXT PLAN

> > **Historical Design Note (superseded):** This document is a legacy implementation plan.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory Context Implementation Plan for Tandem

> **Historical Design Note (superseded):** This document is a legacy implementation plan.
> Current behavior for `v0.3.25+` is global always-on memory with durable SQLite + FTS5 persistence, automatic ingestion/retrieval, and new memory observability events.
> For current contracts and release behavior, use:
>
> - `contracts/http.md`
> - `contracts/events.json`
> - `docs/design/MEMORY_TIERS.md`
> - `docs/RELEASE_NOTES.md`

## Executive Summary

This document outlines a comprehensive plan for adding **Semantic Memory** to Tandem.
The solution involves extracting memory logic into a shared crate (`crates/tandem-memory`) to be used by both the Tauri App and the TUI/CLI, ensuring a unified "Brain" for the agent.

> **Status Update (2026-02-15):** A memory system already exists in `src-tauri/src/memory/`. This plan has been updated to reflect the current implementation and identify remaining gaps.

## Current Implementation Status

### Already Implemented (`src-tauri/src/memory/`)

| Component         | File            | Status                                           |
| ----------------- | --------------- | ------------------------------------------------ |
| Database Layer    | `db.rs`         | ✅ Complete - SQLite + sqlite-vec                |
| Embedding Service | `embeddings.rs` | ⚠️ Placeholder (deterministic pseudo-embeddings) |
| Memory Manager    | `manager.rs`    | ✅ Complete - store, retrieve, cleanup           |
| Text Chunking     | `chunking.rs`   | ✅ Complete - semantic chunking with overlap     |
| File Indexer      | `indexer.rs`    | ✅ Complete - workspace file indexing            |
| Type Definitions  | `types.rs`      | ✅ Complete - MemoryTier, MemoryChunk, etc.      |

### Current Schema (Already in Production)

```sql
-- Session memory (ephemeral)
CREATE TABLE session_memory_chunks (
    id TEXT PRIMARY KEY,
    content TEXT NOT NULL,
    session_id TEXT NOT NULL,
    project_id TEXT,
    source TEX

*[truncated — see source for full prompt]*