# Openalex Enrichment Poc

> #!/usr/bin/env python3
"""
OpenAlex Enrichment POC - Paper-Based Matching

Tests the paper-based matching approach with 100 papers from June 2025.
Pro

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
OpenAlex Enrichment POC - Paper-Based Matching

Tests the paper-based matching approach with 100 papers from June 2025.
Proves that we can reliably match authors via their position in the author list.

Usage:
    python3 openalex_enrichment_poc.py --dry-run  # Test without writing to Neo4j
    python3 openalex_enrichment_poc.py           # Actually enrich the database
"""

import argparse
import os
import re
import sys
import time
from typing import Dict, List, Optional, Tuple
from difflib import SequenceMatcher

import requests
from neo4j import GraphDatabase

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")

# OpenAlex configuration
OPENALEX_API_BASE = "https://api.openalex.org"
OPENALEX_EMAIL = os.getenv("OPENALEX_EMAIL", "bart@advisorsfoundry.com")

# Matching thresholds
NAME_SIMILARITY_THRESHOLD = 0.75  # 75% similarity required
BATCH_SIZE = 50  # OpenAlex allows up to 50 DOIs per request
REQUEST_DELAY = 0.15  # Be polite (6-7 req/sec)

# Statistics
stats = {
    'papers_processed': 0,
    'papers_found_in_openalex': 0,
    'authors_total': 0,
    'authors_matched': 0,
    'authors_enriched': 0,
    'high_confidence_matches': 0,
    'medium_confidence_matches': 0,
    'low_confidence_matches': 0,
}


def name_similarity(name1: str, name2: str) -> float:
    """Calculate similarity between two author names.

    Handles different formats:
    - "John Smith" vs "Smith, John"
    - "J. Smith" vs "John Smith"
    """
    # Normalize: lowercase, remove extra whitespace
    n1 = ' '.join(name1.lower().split())
    n2 = ' '.join(name2.lower().split())

    # Direct comparison
    direct_sim = SequenceMatcher(None, n1, n2).ratio()

    # Try reversing second name (handle "Last, First" format)
    if ',' in n2:
        parts = n2.split(',')
        reversed_n2 = f"{parts[1].strip()} {parts[0].s

*[truncated — see source for full prompt]*