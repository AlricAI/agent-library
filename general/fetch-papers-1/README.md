# Fetch Papers

> #!/usr/bin/env python3
"""
Stage 1: Fetch ALL AI/ML papers from arXiv.org

This script fetches all papers from arXiv categories related to AI/ML
that 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Stage 1: Fetch ALL AI/ML papers from arXiv.org

This script fetches all papers from arXiv categories related to AI/ML
that were submitted in the last 24 hours. It respects arXiv's rate limit
of 1 request per 3 seconds.

Output: JSON file with complete paper list including all metadata and authors
"""

import argparse
import json
import time
from datetime import datetime, timedelta
from pathlib import Path
from typing import Any

import arxiv


# arXiv categories for AI/ML papers
AI_CATEGORIES = [
    "cs.AI",  # Artificial Intelligence
    "cs.LG",  # Machine Learning
    "cs.CV",  # Computer Vision
    "cs.CL",  # Computation and Language (NLP)
    "stat.ML",  # Statistics - Machine Learning
]


def build_arxiv_query(target_date: datetime) -> str:
    """
    Build arXiv API query for AI/ML papers submitted on target_date.

    Format: (cat:cs.AI OR cat:cs.LG ...) AND submittedDate:[start TO end]
    """
    # Query papers submitted on the target date (24-hour window)
    start_date = target_date.strftime("%Y%m%d0000")
    end_date = target_date.strftime("%Y%m%d2359")

    category_query = " OR ".join([f"cat:{cat}" for cat in AI_CATEGORIES])
    date_query = f"submittedDate:[{start_date} TO {end_date}]"

    return f"({category_query}) AND {date_query}"


def extract_paper_metadata(result: arxiv.Result) -> dict[str, Any]:
    """Extract all relevant metadata from an arXiv paper result."""

    # Extract arxiv_id (remove version suffix for consistency)
    arxiv_id = result.entry_id.split("/")[-1]  # e.g., "2501.12345v1"

    # Extract authors as list of dicts with name and affiliation
    authors = []
    for author in result.authors:
        authors.append({
            "name": author.name,
            # Note: arxiv API doesn't provide affiliations, set to None
            # We can enrich this later via other sources
            "affiliation": None,
        })

    # Extract categories as list
    categories = result.categories

    # Bu

*[truncated — see source for full prompt]*