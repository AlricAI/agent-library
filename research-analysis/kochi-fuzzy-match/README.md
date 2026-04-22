# Kochi Fuzzy Match

> #!/usr/bin/env python3
"""
Kochi Fuzzy Matching - Simplified Version

Matches authors from new papers to existing authors in Neo4j database
using cont

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Kochi Fuzzy Matching - Simplified Version

Matches authors from new papers to existing authors in Neo4j database
using contextual signals (co-authors, affiliation, research area).

Usage:
    python3 kochi_fuzzy_match.py --date 2025-10-12
    python3 kochi_fuzzy_match.py --date-start 2025-10-01 --date-end 2025-10-31
    python3 kochi_fuzzy_match.py --arxiv-ids 2510.12345v1,2510.12346v1
    python3 kochi_fuzzy_match.py --all --limit 100
"""

import argparse
import os
import sys
import uuid
from datetime import datetime
from typing import List, Dict, Optional, Set
from dataclasses import dataclass

from neo4j import GraphDatabase

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")

# Matching thresholds
CONFIDENCE_THRESHOLD_MERGE = 80  # Use existing author
CONFIDENCE_THRESHOLD_LINK = 60   # Create new + mark POSSIBLY_SAME_AS
MAX_SCORE = 100

# Signal weights (simplified version - 3 signals)
WEIGHT_COAUTHOR_2_PLUS = 50
WEIGHT_COAUTHOR_1 = 25
WEIGHT_NAME_AFFILIATION = 30
WEIGHT_RESEARCH_AREA_2_PLUS = 20


@dataclass
class MatchResult:
    """Result of fuzzy matching between new author and candidate."""
    candidate_kid: str
    candidate_name: str
    confidence: int
    signals: List[str]
    reasoning: str


@dataclass
class AuthorAction:
    """Decision on what to do with a new author."""
    action: str  # 'USE_EXISTING', 'CREATE_WITH_LINK', 'CREATE_NEW'
    existing_kid: Optional[str] = None
    possible_duplicate_kid: Optional[str] = None
    confidence: int = 0
    reasoning: str = ""


class KochiFuzzyMatcher:
    """Simplified Kochi Fuzzy Matching engine."""

    def __init__(self, driver):
        self.driver = driver
        self.database = NEO4J_DATABASE

    def find_author_candidates(self, author_name: str) -> List[Dict]:
        """
        Find existing authors with same or simi

*[truncated — see source for full prompt]*