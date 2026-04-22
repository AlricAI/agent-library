# S2 Enrichment Backfill

> #!/usr/bin/env python3
"""
Semantic Scholar Author ID Backfill Script (Continuous Mode)

Enriches Author nodes with S2 author IDs by querying papers f

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Semantic Scholar Author ID Backfill Script (Continuous Mode)

Enriches Author nodes with S2 author IDs by querying papers from S2 API.
Uses position-based matching to link our authors to S2 author IDs.

Features:
- Automatic: Finds all unenriched papers and processes them
- Continuous: Processes in chunks, moves to next chunk automatically
- Resumable: Checkpoint system - Ctrl+C anytime, resume later
- Non-destructive: Only adds s2_author_id field
- Direction: Always newest to oldest (strictly backwards)

Usage:
    # Continuous mode (always backwards: newest → oldest)
    python3 s2_enrichment_backfill.py

    # With custom chunk size (default: 2 months at a time)
    python3 s2_enrichment_backfill.py --month-chunk 3

    # Manual date range override
    python3 s2_enrichment_backfill.py --start-date 2024-02-14 --end-date 2025-10-15

    # Dry run
    python3 s2_enrichment_backfill.py --dry-run

Resume:
    If interrupted (Ctrl+C or error), just run the same command again.
    It will automatically resume from the last checkpoint with the same direction.
"""

import argparse
import json
import os
import sys
import time
from datetime import datetime, timedelta
from pathlib import Path
from typing import Dict, List, Optional, Tuple
from neo4j import GraphDatabase
import requests

# Try to load .env.local if environment variables not set
if not os.getenv("SEMANTIC_SCHOLAR_API_TOKEN"):
    current_dir = Path(__file__).parent
    for _ in range(3):
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
        

*[truncated — see source for full prompt]*