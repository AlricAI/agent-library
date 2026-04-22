# Test S2 Disambiguation

> #!/usr/bin/env python3
"""
Semantic Scholar Author Disambiguation Test

Tests S2's author disambiguation against our fuzzy matching results.
Analyzes 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Semantic Scholar Author Disambiguation Test

Tests S2's author disambiguation against our fuzzy matching results.
Analyzes coverage, accuracy, and conflicts.

Usage:
    python3 test_s2_disambiguation.py --days 3 --dry-run
    python3 test_s2_disambiguation.py --days 7 --limit 100
    python3 test_s2_disambiguation.py --output results.json
"""

import argparse
import json
import os
import sys
import time
from datetime import datetime, timedelta
from typing import Dict, List, Optional
from pathlib import Path
from neo4j import GraphDatabase
import requests

# Try to load .env.local if environment variables not set
if not os.getenv("SEMANTIC_SCHOLAR_API_TOKEN"):
    # Look for .env.local in parent directories
    current_dir = Path(__file__).parent
    for _ in range(3):  # Look up 3 levels
        env_file = current_dir / ".env.local"
        if env_file.exists():
            print(f"📋 Loading environment from {env_file}")
            with open(env_file) as f:
                for line in f:
                    line = line.strip()
                    if line and not line.startswith('#') and '=' in line:
                        key, value = line.split('=', 1)
                        if key not in os.environ:
                            os.environ[key] = value
            break
        current_dir = current_dir.parent

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")

# Semantic Scholar configuration
S2_API_KEY = os.getenv("SEMANTIC_SCHOLAR_API_TOKEN")
S2_API_BASE = "https://api.semanticscholar.org/graph/v1"
S2_RATE_LIMIT = 2.0  # Seconds between requests (very conservative for 1 req/sec limit)


class SemanticScholarClient:
    """Client for Semantic Scholar API with rate limiting."""

    def __init__(self, api_key: str):
        self.api_key = api_key
        self.last_request_time = time.t

*[truncated — see source for full prompt]*