# Instapaper Ingestion Design

> > **Note**: This document was provided by the project owner on *2025-07-11* and copied here verbatim so the full design lives inside the repository.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
    │   └──

*[truncated — see source for full prompt]*