# README

> **Daily curated AI research papers from arXiv.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# arXiv Research Agent

**Daily curated AI research papers from arXiv.org with author intelligence tracking**

## Overview

The arXiv Research Agent is an autonomous daily agent that:
1. **Fetches ALL** AI/ML papers from arXiv.org (cs.AI, cs.LG, cs.CV, cs.CL, stat.ML)
2. **Stores ALL** papers with complete author tracking in a relational database
3. **Curates** the top 5-10 most significant papers using Claude Agent SDK
4. **Generates** a professional markdown report with curation reasoning
5. **Broadcasts** the curated digest to SMS subscribers daily at 6 AM PT
6. **Builds intelligence** over time: author notability scores, publication patterns, research trends

## Architecture

### Two-Stage Process

#### Stage 1: Fetch All Papers (`fetch_papers.py`)
- Uses official `arxiv` Python library
- Queries ALL papers submitted in last 24 hours
- Respects arXiv rate limit: **1 request per 3 seconds**
- Extracts full metadata: title, abstract, authors, categories, URLs
- Outputs JSON file with complete paper list

#### Stage 2: Curate & Report (`agent.py`)
- Uses **Claude Agent SDK** for autonomous curation
- Analyzes papers against 5 criteria:
  - Novelty (30%)
  - Impact Potential (25%)
  - Author Notability (20%)
  - Research Quality (15%)
  - Timeliness (10%)
- Selects top 5-10 papers with reasoning
- Generates 3-5 page markdown report
- Outputs featured paper metadata

#### TypeScript Orchestrator (`index.ts`)
- Runs both Python stages
- Stores ALL papers to database
- Upserts ALL authors
- Links papers to authors (many-to-many)
- Marks featured papers
- Calculates author notability scores
- Uploads report to Supabase Storage
- Returns metadata for SMS broadcasting

## Database Schema

### Tables Created

#### `arxiv_papers`
Stores ALL papers fetched from arXiv with significance signals:
- `arxiv_id` (PK) - e.g., "2501.12345v1"
- `title`, `abstract`, `categories[]`, `published_date`
- `arxiv_url`, `pdf_url`
- `author_notability_score` - Sum of all authors' scores
- `fe

*[truncated — see source for full prompt]*