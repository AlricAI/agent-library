# VISION AND ARCHITECTURE

> ## What We Are Building

`nyc-housing-scout` is a local-first pipeline for collecting housing posts from Facebook groups, storing them durably, extrac

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Vision and Architecture

## What We Are Building

`nyc-housing-scout` is a local-first pipeline for collecting housing posts from Facebook groups, storing them durably, extracting structured housing data, and serving that data through both local operator surfaces and a future hosted public frontend.

The goal is not just to scrape pages. The goal is to build a system that can:

- keep up with ongoing post volume across multiple groups
- run continuously on one always-on laptop with minimal operator intervention
- keep several authenticated group feeds healthy in parallel without cross-source confusion
- avoid reprocessing the same posts unnecessarily
- extract structured housing data reliably from messy free-form posts
- preserve enough provenance to debug or reprocess later
- stay simple, modular, and operable by one person on one machine

## Product Shape

The system should support a workflow like this:

1. keep one or more configured Facebook sources attached to healthy authenticated browser tabs
2. sweep those sources continuously and incrementally
3. persist raw observations and canonical post state locally
4. queue unprocessed posts for extraction
5. process posts into structured listing data
6. expose local operator views for inspection, review, and debugging
7. publish a curated hosted read model for a public-facing frontend

## Guiding Principles

### 1. Each pipeline stage should stand alone
Every major stage should be independently operable and testable.

Examples:
- scrape latest 5 posts from one source
- inspect newly collected posts
- enqueue unprocessed posts for extraction
- dry-run extraction on N queued posts
- store processed output without running the crawler

This means each stage should have its own CLI surface and clear input/output contract.

### 2. Local SQLite is the canonical write-side
Use local SQLite for operational state and queryable application data.

Use files on disk for:
- raw artifacts
- collected/listing exports
- debugging an

*[truncated — see source for full prompt]*