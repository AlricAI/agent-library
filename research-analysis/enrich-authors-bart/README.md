# Enrich Authors Bart

> #!/usr/bin/env python3
"""
Author Enrichment Agent - Fetch GitHub stars and OpenAlex data

This script enriches Author nodes in Neo4j with:
1. GitHub 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Author Enrichment Agent - Fetch GitHub stars and OpenAlex data

This script enriches Author nodes in Neo4j with:
1. GitHub stars - extracted from paper abstracts, aggregated per author
2. OpenAlex data - affiliations, h-index, citations

Usage:
    python3 enrich_authors.py --arxiv-ids 2501.12345v1,2501.12346v1
    python3 enrich_authors.py --all  # Process all papers in database
"""

import argparse
import os
import re
import sys
import time
from collections import defaultdict
from typing import Dict, List, Set, Optional
from urllib.parse import urlparse

import requests
from neo4j import GraphDatabase

# GitHub API configuration
GITHUB_API_BASE = "https://api.github.com"
GITHUB_TOKEN = os.getenv("GITHUB_API_TOKEN")

# OpenAlex API configuration
OPENALEX_API_BASE = "https://api.openalex.org"
OPENALEX_EMAIL = os.getenv("OPENALEX_EMAIL", "bart@advisorsfoundry.com")  # For polite pool (10 req/sec)

# Rate limiting and retry configuration
MAX_RETRIES = 5
BASE_DELAY = 1  # seconds
MAX_DELAY = 32  # seconds
REQUEST_DELAY = 0.1  # Base delay between requests (10 req/sec with polite pool)
BATCH_SIZE = 50  # OpenAlex allows up to 50 IDs per request

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")

# Institution tier mapping (for notability bonus)
TIER_1_INSTITUTIONS = {
    "openai", "deepmind", "google brain", "meta ai", "fair",
    "microsoft research", "anthropic", "stanford", "mit",
    "berkeley", "carnegie mellon", "cmu"
}

TIER_2_INSTITUTIONS = {
    "harvard", "princeton", "yale", "oxford", "cambridge",
    "toronto", "nyu", "cornell", "ucla", "ucsd", "uw", "washington"
}


def extract_github_repos_from_abstract(abstract: str) -> List[str]:
    """Extract GitHub repository URLs from paper abstract."""
    # Match github.com/username/repo (with various URL formats)
    pattern = r'github\.c

*[truncated — see source for full prompt]*