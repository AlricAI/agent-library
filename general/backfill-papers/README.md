# Backfill Papers

> #!/usr/bin/env python3
"""
Batch backfill arXiv AI/ML papers into Neo4j over a multi-month window.

Each run ingests up to a fixed number of papers (d

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Batch backfill arXiv AI/ML papers into Neo4j over a multi-month window.

Each run ingests up to a fixed number of papers (default 20000), marching
backward in time. The script records its progress in a state file so
subsequent executions resume from the previous stopping point until the
target lookback window (default 12 months) is fully covered.
"""

from __future__ import annotations

import argparse
import json
import logging
from dataclasses import dataclass
from datetime import date, datetime, timedelta, timezone
from pathlib import Path
from typing import Any

import arxiv
from neo4j import GraphDatabase
from neo4j.exceptions import Neo4jError
from neo4j.time import Date as Neo4jDate

from load_recent_papers import (  # local import
    AI_CATEGORIES,
    ConfigurationError,
    Neo4jConfig,
    load_papers_into_neo4j,
    read_config_from_env,
)

DEFAULT_LIMIT = 20000
DEFAULT_LOOKBACK_DAYS = 1095  # ≈ 36 months
STATE_FILENAME = "backfill_state.json"


@dataclass
class BackfillState:
    anchor_date: date
    last_end_date: date
    earliest_ingested: date | None
    completed: bool

    @classmethod
    def load(cls, path: Path) -> BackfillState | None:
        if not path.exists():
            return None
        data = json.loads(path.read_text())
        return cls(
            anchor_date=datetime.strptime(data["anchor_date"], "%Y-%m-%d").date(),
            last_end_date=datetime.strptime(data["last_end_date"], "%Y-%m-%d").date(),
            earliest_ingested=(
                datetime.strptime(data["earliest_ingested"], "%Y-%m-%d").date()
                if data.get("earliest_ingested")
                else None
            ),
            completed=bool(data.get("completed", False)),
        )

    def save(self, path: Path) -> None:
        payload = {
            "anchor_date": self.anchor_date.isoformat(),
            "last_end_date": self.last_end_date.isoformat(),
            "earliest_ingested": self.earliest_ingested.i

*[truncated — see source for full prompt]*