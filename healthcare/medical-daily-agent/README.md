# Medical Daily Agent

> """
Medical Daily Agent - Demo Script
Fetches medical research, generates summaries, and creates audio podcasts
"""

import os
import json
impo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Medical Daily Agent - Demo Script
Fetches medical research, generates summaries, and creates audio podcasts
"""

import os
import json
import random
import requests
from datetime import datetime, timedelta
from typing import List, Dict, Optional
import xml.etree.ElementTree as ET
from pathlib import Path
import shutil
import html
import re

TTS_CHAR_LIMIT = 4096
TTS_SAFE_LIMIT = 3800  # leave room for metadata

# === PubMed recency defaults ===
# Adjust these constants to change the default recency filter without touching the class.
# - PUBMED_DEFAULT_MAX_AGE_DAYS: 0 keeps only today's articles, N keeps the last N days,
#   negative numbers remove the age limit entirely.
# - PUBMED_DEFAULT_SEARCH_WINDOW_DAYS: controls the PubMed `reldate` window scanned for
#   candidates; keep this positive to ensure results.
PUBMED_DEFAULT_MAX_AGE_DAYS = 0
PUBMED_DEFAULT_SEARCH_WINDOW_DAYS = 2

# === Headline topic hints ===
# Maps common medical keywords to gentle, listener-friendly topic labels.
HEADLINE_TOPIC_HINTS = [
    ("Cancer breakthroughs", {"oncology", "cancer", "tumor", "carcinoma", "melanoma", "leukemia"}),
    ("Heart health", {"cardio", "heart", "cardiac", "cholesterol", "hypertension"}),
    ("Brain and nerves", {"neuro", "brain", "parkinson", "alzheimer", "stroke", "psychi"}),
    ("Metabolic health", {"diabetes", "metabolic", "obesity", "glp-1", "insulin"}),
    ("Immune therapies", {"immun", "vaccine", "antibody", "immune", "autoimmune"}),
    ("Gene and cell therapy", {"gene", "cell", "crispr", "genome", "rna", "stem"}),
    ("Aging and longevity", {"aging", "longevity", "senolytic", "anti-aging", "lifespan"}),
    ("Digital medicine", {"digital", "ai ", "machine learning", "wearable", "app", "telemed"}),
    ("Rare diseases", {"rare", "orphan", "ultra-rare"}),
    ("Clinical trial results", {"phase", "trial", "study", "randomized"}),
]

# === Breakthrough scoring knobs ===
# Boost terms tied to pivotal results a

*[truncated — see source for full prompt]*