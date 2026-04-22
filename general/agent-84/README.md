# Agent

> import argparse
import json
import os
from datetime import datetime
from pathlib import Path
from typing import Any, Dict, Iterable, List, Optional

f

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import argparse
import json
import os
from datetime import datetime
from pathlib import Path
from typing import Any, Dict, Iterable, List, Optional

from medical_daily_agent import MedicalDailyAgent


def parse_args() -> argparse.Namespace:
    parser = argparse.ArgumentParser(
        description='Run the Medical Daily agent and emit report metadata.'
    )
    parser.add_argument(
        '--output-dir',
        required=True,
        help='Directory where markdown and metadata files will be written.'
    )
    parser.add_argument(
        '--cache-dir',
        help='Directory used for cached assets (defaults to <output-dir>/cache).'
    )
    parser.add_argument(
        '--date',
        help='Override ISO date (YYYY-MM-DD) used for filenames.'
    )
    parser.add_argument(
        '--model',
        default=os.getenv('MEDICAL_DAILY_MODEL', 'gpt-4o'),
        help='Override the LLM model used for summarisation.'
    )
    parser.add_argument(
        '--max-age-days',
        type=int,
        help='Override PubMed recency filter (max age in days).'
    )
    parser.add_argument(
        '--search-window-days',
        type=int,
        help='Override PubMed search window size.'
    )
    return parser.parse_args()


def ensure_directory(path: Path) -> Path:
    path.mkdir(parents=True, exist_ok=True)
    return path


def clip_text(text: str, limit: int = 320) -> str:
    compact = ' '.join(text.split())
    if len(compact) <= limit:
        return compact

    truncated = compact[:limit]
    if '.' in truncated:
        truncated = truncated.rsplit('.', 1)[0].strip()
        if truncated:
            return truncated + '.'

    return truncated.rstrip() + '...'


def extract_summary(articles: Iterable[Dict[str, Any]]) -> str:
    for article in articles:
        if not isinstance(article, dict):
            continue
        for key in ('podcast_summary', 'detail_summary', 'summary', 'description'):
            value = article.get(key)
            if isinstan

*[truncated — see source for full prompt]*