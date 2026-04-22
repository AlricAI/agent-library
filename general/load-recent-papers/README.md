# Load Recent Papers

> #!/usr/bin/env python3
"""
Fetch up to a week of AI/ML papers from arXiv and load them into Neo4j.

This utility is intended for the Neo4j fork of the

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Fetch up to a week of AI/ML papers from arXiv and load them into Neo4j.

This utility is intended for the Neo4j fork of the arXiv Research Agent.
It pulls papers across the core AI categories over a configurable date
window and stores Paper, Author, and Category nodes plus relationships.
"""

from __future__ import annotations

import argparse
import json
import logging
import os
from dataclasses import dataclass
from datetime import date, datetime, timedelta, timezone
from pathlib import Path
from typing import Any, Iterable, List

import arxiv
from neo4j import GraphDatabase
from neo4j.exceptions import Neo4jError

# Reuse the same category coverage as the relational agent
AI_CATEGORIES = [
    "cs.AI",
    "cs.LG",
    "cs.CV",
    "cs.CL",
    "stat.ML",
]
DEFAULT_MAX_RESULTS = 1000
DEFAULT_DAYS = 7
BATCH_SIZE = 25

MERGE_BATCH_QUERY = """
UNWIND $batch AS paper
MERGE (p:Paper {arxiv_id: paper.arxiv_id})
ON CREATE SET
    p.created_at = datetime(paper.ingested_at),
    p.featured_in_report = false,
    p.featured_rank = null,
    p.curation_reason = null,
    p.featured_date = null,
    p.author_notability_score = coalesce(p.author_notability_score, 0)
SET p.title = paper.title,
    p.abstract = paper.abstract,
    p.categories = paper.categories,
    p.primary_category = paper.primary_category,
    p.published_date = date(paper.published_date),
    p.arxiv_url = paper.arxiv_url,
    p.pdf_url = paper.pdf_url,
    p.updated_at = datetime(paper.ingested_at),
    p.last_ingested_at = datetime(paper.ingested_at)
WITH p, paper
FOREACH (category IN paper.categories |
  MERGE (c:Category {name: category})
  MERGE (p)-[:IN_CATEGORY]->(c)
)
WITH p, paper
FOREACH (author_map IN paper.authors |
  // CREATE new Author node for each authorship (not MERGE)
  // Each paper appearance gets its own Author node with unique KID
  CREATE (a:Author)
  SET a.kochi_author_id = 'KA_' + substring(randomUUID(), 0, 12),
      a.name = author_map.name,
      a.a

*[truncated — see source for full prompt]*