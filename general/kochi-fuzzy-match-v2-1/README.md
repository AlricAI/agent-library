# Kochi Fuzzy Match V2

> #!/usr/bin/env python3
"""
Kochi Fuzzy Matching V2 - Authorship-based Model

Assigns canonical_kid to Author nodes based on fuzzy matching.

In the ne

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Kochi Fuzzy Matching V2 - Authorship-based Model

Assigns canonical_kid to Author nodes based on fuzzy matching.

In the new authorship-based model:
- Each paper appearance creates a NEW Author node with unique KID
- Fuzzy matching determines which Author nodes represent the same person
- Sets canonical_kid field to link related Author nodes

Features:
- Works backwards in time (newest to oldest papers)
- Progress updates every 5 minutes with rate and ETA
- Checkpoint system saves progress every 100 authors
- Safe to stop at any time (Ctrl+C) - no data loss
- Automatically resumes from last checkpoint

Usage:
    python3 kochi_fuzzy_match_v2.py --all                    # Process all authors needing canonical_kid
    python3 kochi_fuzzy_match_v2.py --date 2025-10-12 --dry-run
    python3 kochi_fuzzy_match_v2.py --date-start 2025-10-01 --date-end 2025-10-31
    python3 kochi_fuzzy_match_v2.py --paper-date-start 2025-09-01 --paper-date-end 2025-10-31
"""

import argparse
import json
import os
import sys
import time
from datetime import datetime
from pathlib import Path
from typing import List, Dict, Optional, Set
from dataclasses import dataclass

from neo4j import GraphDatabase
from neo4j.exceptions import SessionExpired, ServiceUnavailable

# Neo4j configuration
NEO4J_URI = os.getenv("NEO4J_URI")
NEO4J_USERNAME = os.getenv("NEO4J_USERNAME")
NEO4J_PASSWORD = os.getenv("NEO4J_PASSWORD")
NEO4J_DATABASE = os.getenv("NEO4J_DATABASE", "neo4j")

# Matching thresholds
CONFIDENCE_THRESHOLD_CANONICAL = 80  # Assign to canonical author
CONFIDENCE_THRESHOLD_UNCERTAIN = 60  # Flag as uncertain, needs review
MAX_SCORE = 100

# Signal weights (3 signals)
WEIGHT_COAUTHOR_2_PLUS = 50
WEIGHT_COAUTHOR_1 = 25
WEIGHT_NAME_AFFILIATION = 30
WEIGHT_RESEARCH_AREA_2_PLUS = 20
WEIGHT_RESEARCH_AREA_1 = 10

# Connection management
RECONNECT_AFTER_AUTHORS = 500  # Refresh connection every N authors
MAX_RETRIES = 3  # Retry failed operations
RETRY_DELAY = 2  # Seconds to

*[truncated — see source for full prompt]*