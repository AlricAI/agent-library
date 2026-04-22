# SIMPLE PODCAST FIX

> ## CURRENT STATUS: SUPERSEDED BY MAIN PIPELINE

This document outlines a simplified, proof-of-concept approach for podcast processing. The core functi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SIMPLE PODCAST FIX - QWEN CODE COMPATIBLE

## CURRENT STATUS: SUPERSEDED BY MAIN PIPELINE

This document outlines a simplified, proof-of-concept approach for podcast processing. The core functionality described here has been fully integrated and expanded upon in the main `SmartTranscriptionPipeline` (`helpers/smart_transcription_pipeline.py`).

For the complete and robust podcast ingestion and transcription system, please refer to `PODCAST_PROCESSING_MASTER_PLAN.md` and the `smart_transcription.py` script.

## THE PROBLEM
*(Note: These problems have been addressed by the main `SmartTranscriptionPipeline`.)*
- Database has 6 articles ABOUT podcasts, not actual episodes (now handles real episodes).
- No RSS feed ingestion exists (now integrated).
- Scheduler runs 3 minutes then exits (now continuous processing and queuing).

## SIMPLE 3-STEP FIX

### STEP 1: Create Simple RSS Importer

**File: `simple_rss_import.py`**
```python
#!/usr/bin/env python3
import feedparser
import sqlite3
import requests

# Simple RSS feed importer - run once to populate episodes
feeds = {
    "Acquired": "https://feeds.simplecast.com/7wT59F0l",
    "99% Invisible": "https://feeds.99percentinvisible.org/99percentinvisible",
    "This American Life": "https://feeds.thisamericanlife.org/talpodcast",
    "Radiolab": "https://feeds.feedburner.com/radiolab",
    "ATP": "https://atp.fm/rss"
}

def import_episodes():
    # Create table
    with sqlite3.connect("data/atlas.db") as conn:
        conn.execute("""
            CREATE TABLE IF NOT EXISTS podcast_episodes (
                id INTEGER PRIMARY KEY,
                title TEXT,
                audio_url TEXT UNIQUE,
                podcast_name TEXT,
                processed BOOLEAN DEFAULT 0
            )
        """)

        total = 0
        for name, url in feeds.items():
            print(f"Importing {name}...")
            feed = feedparser.parse(url)

            for entry in feed.entries[:10]:  # Only 10 per podcast for testing
 

*[truncated — see source for full prompt]*