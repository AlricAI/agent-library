# README

> **Daily arXiv AI research briefings backed by a Neo4j knowledge graph**

## Overview

This variant of the arXiv agent keeps the existing Claude-based 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# arXiv Research Graph Agent

**Daily arXiv AI research briefings backed by a Neo4j knowledge graph**

## Overview

This variant of the arXiv agent keeps the existing Claude-based curation loop,
but swaps the relational storage layer for a Neo4j Aura graph. Every run:

1. Fetches 24 hours of cs.AI / cs.LG / cs.CV / cs.CL / stat.ML papers.
2. Loads Paper, Author, and Category nodes (plus AUTHORED / IN_CATEGORY edges) into Neo4j.
3. Runs the Claude curation agent to pick the top papers and write the report.
4. Marks featured papers in the graph, recomputes author notability scores, and stores a Report node with metadata + FEATURED_IN edges.
5. Uploads the markdown report to Supabase Storage and records the viewer/podcast links in Neo4j.

Trigger it from SMS with `ARXIV-GRAPH` or `ARXIV-GRAPH RUN`, or call
`runAndStoreArxivGraphReport()` directly from code/tests.

## Architecture

### Stage 1 – Fetch & Load

1. `agents/arxiv-research/fetch_papers.py` pulls the last 24h of submissions (respecting the 3 s rate limit).
2. The TypeScript orchestrator writes a deduped JSON bundle for the target date.
3. The orchestrator enriches each paper with live Neo4j author stats (notability score, paper count, featured streak, first/last seen) so Claude has reputation context before ranking breakthroughs.
4. `agents/arxiv-research-graph/load_recent_papers.py --input-json` ingests the enriched bundle into Neo4j using batched Cypher merges.

### Stage 2 – Curate & Persist

1. `agents/arxiv-research/agent.py` (Claude Agent SDK) generates the markdown report and featured paper metadata, using the enriched author signals already embedded in the JSON.
2. `graph-dao.ts` updates Neo4j:
   - `Paper` nodes get `featured_in_report`, `featured_rank`, `curation_reason`, `featured_date`, `star_rating`, and refreshed `author_notability_score`.
   - `Author` nodes recalc `paper_count`, `featured_paper_count`, and `notability_score` using the existing formula.
   - A `Report` node (unique per date) st

*[truncated — see source for full prompt]*