# Openalex Enrichment Backfill

> #!/usr/bin/env python3
"""
OpenAlex Enrichment Backfill - Continuous Mode

Enriches canonical authors in Neo4j with OpenAlex data using paper-based ma

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
OpenAlex Enrichment Backfill - Continuous Mode

Enriches canonical authors in Neo4j with OpenAlex data using paper-based matching.
Uses proven approach: match authors via paper DOI + author position (not unreliable name search).

Features:
- Automatic: Finds all unenriched papers and processes them
- Continuous: Processes in chunks, moves to next chunk automatically
- Resumable: Checkpoint system - Ctrl+C anytime, resume later
- Non-destructive: Only adds openalex_* fields
- Direction: Oldest to newest (better OpenAlex coverage)
- Batch processing (50 papers per OpenAlex API call)
- Connection retry logic (handles Neo4j timeouts)

Usage:
    # Continuous mode (recommended) - just let it run!
    python3 openalex_enrichment_backfill.py

    # With custom chunk size (default: 2 months at a time)
    python3 openalex_enrichment_backfill.py --month-chunk 3

    # Manual date range override
    python3 openalex_enrichment_backfill.py --start-date 2024-02-14 --end-date 2025-06-30

    # Force re-enrichment (update old data)
    python3 openalex_enrichment_backfill.py --force

    # Dry run
    python3 openalex_enrichment_backfill.py --dry-run

Resume:
    If interrupted (Ctrl+C or error), just run the same command again.
    It will automatically resume from the last checkpoint.

Expected Results:
    - Papers processed: ~127,248 (Feb 2024 - June 2025)
    - Papers in OpenAlex: ~89,000 (70% coverage)
    - Authors enriched: ~67,000 (high confidence via paper-position matching)
"""

import argparse
import json
import os
import re
import sys
import time
from datetime import date, datetime, timedelta
from difflib import SequenceMatcher
from pathlib import Path
from typing import Dict, List, Optional, Set, Tuple

import requests
from neo4j import GraphDatabase
from neo4j.exceptions import Neo4jError, ServiceUnavailable, SessionExpired

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWOR

*[truncated — see source for full prompt]*