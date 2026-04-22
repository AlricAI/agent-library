---
name: Instapaper Ingestion Design
description: > **Note**: This document was provided by the project owner on *2025-07-11* and copied here verbatim so the full design lives inside the repository.
model: claude-sonnet-4-5
---
## 📚 Instapaper Ingestion Module – Full Integration Design

> **Note**: This document was provided by the project owner on *2025-07-11* and copied here verbatim so the full design lives inside the repository.  It has not yet been fully implemented – see the TODO section at the end for next steps.

---

### 🧭 Overview

This module is responsible for fetching, storing, and processing all articles saved to an Instapaper account. It supports both **initial full export** and **incremental updates**, using either credentials or OAuth 1.0a. All output is stored locally in a structured format, ready for downstream processing by the Atlas ingest pipeline.

---

### 🎯 Goals

- Pull all saved bookmarks from Instapaper using their public API.
- Store both raw and normalized versions of the data locally.
- Deduplicate entries using unique Instapaper `hash` values or URLs.
- Output clean files (CSV or JSONL) for use in Atlas ingestion.
- Allow manual future syncing by re-running the script with diff logic.
- Preserve folder/tag metadata for future categorization or training.

---

### 🔐 Required .env Values

```env
# For basic auth (recommended for one-time pull)
INSTAPAPER_USERNAME=you@example.com
INSTAPAPER_PASSWORD=yourpassword

# Or for OAuth 1.0a (more secure if syncing long-term)
INSTAPAPER_CONSUMER_KEY=your_key
INSTAPAPER_CONSUMER_SECRET=your_secret
INSTAPAPER_ACCESS_TOKEN=token
INSTAPAPER_ACCESS_SECRET=secret

# Always required
INSTAPAPER_API_BASE=https://www.instapaper.com/api/1
```

---

### 🧱 API Capabilities
* `/bookmarks/list` – fetch all bookmarks
* `/bookmarks/list?have=` – skip previously-seen items via hash
* `/folders/list` – (optional) folder metadata
* `/bookmarks/get_text` – (optional) clean article text

Returned fields per item: `title`, `url`, `description`, `hash`, `time`, `progress`, `starred`, `folder_id` …

---

### 📁 Directory Structure
```
input/
└── instapaper/
    ├── raw/
    │   └── instapaper_full_2025-07-11.json
    ├── clean/
    │   └── clean_instapaper_2025-07-11.csv
    ├── hashes/
    │   └── instapaper_hashes.txt
    └── archive/
        └── (optional backup of older files)
```

---

### 🧩 Ingest Logic (Step-by-Step)
1. **Authenticate** – basic auth or OAuth.
2. **Fetch All Bookmarks** – `GET /bookmarks/list` + pagination; store raw JSON.
3. **Deduplicate** – compare `hash` against local `hashes/instapaper_hashes.txt`.
4. **Normalize** – extract `title`, `url`, `folder_title`, `created_at`, `hash` …
5. **Write Output** – `raw/`, `clean/`, `hashes/`.
6. **Feed to Atlas** – pass each normalized link into central ingest dispatcher.

---

### 🔁 Optional Syncing Strategy
* On future runs use `?have=` with saved hashes to fetch only new items.
* Hash list stored in flat file is sufficient; no DB required.

---

### 🤖 Automation Tips
* Schedule via cron or run manually.
* Future upgrade: Playwright auto-login + export.

---

### 📌 Questions / Decisions Outstanding
* Parse full article via `bookmarks/get_text` now or defer to Atlas?
* Map folders to tags or keep as metadata?
* Include timestamps / device info?
* How to dedupe across RSS + Instapaper duplicates?
* Unify all link ingestion via a `unified_link_ingestor.py`?

---

### ✅ Done When
* All bookmarks fetched & stored.
* Normalized files saved under `input/instapaper/`.
* Atlas ingestion ready (or triggered).
* Future syncs skip duplicates via hash file.

---

### TODO (tracked via GitHub issues / TODO list)
- [ ] Implement `instapaper_api_export.py` following this spec
- [ ] Add incremental sync flag & hash storage
- [ ] Decide on folder→tag mapping strategy
- [ ] Wire export output into main ingest dispatcher