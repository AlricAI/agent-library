# Api Documentation

> This document describes all major API endpoints for Atlas, including ingestion, scheduling, and cognitive amplification (Ask) features.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas API Documentation

This document describes all major API endpoints for Atlas, including ingestion, scheduling, and cognitive amplification (Ask) features.

## 🧠 Cognitive Amplification (Ask) API

### Proactive Surfacer
- **GET** `/ask/proactive`
- **Description:** Surfaces forgotten/stale content for review or re-engagement.
- **Response Example:**
```json
{
  "forgotten": [
    {"title": "Example Article", "updated_at": "2025-06-01T12:00:00"},
    ...
  ]
}
```

### Temporal Engine
- **GET** `/ask/temporal`
- **Description:** Shows time-aware relationships between content items.
- **Response Example:**
```json
{
  "relationships": [
    {"from": "Article A", "to": "Article B", "days": 2},
    ...
  ]
}
```

### Socratic Question Generator
- **POST** `/ask/socratic`
- **Parameters:**
  - `content` (form field, required): The text to generate questions from.
- **Description:** Generates Socratic questions from submitted content.
- **Request Example:**
```bash
curl -X POST -F "content=The sky is blue." https://atlas.khamel.com/ask/socratic
```
- **Response Example:**
```json
{
  "questions": [
    "Why is 'The sky is blue' important?",
    "What are the implications of 'The sky is blue'?",
    ...
  ]
}
```

### Active Recall Engine
- **GET** `/ask/recall`
- **Description:** Shows most overdue items for spaced repetition review.
- **Response Example:**
```json
{
  "due_for_review": [
    {"title": "Example Note", "last_reviewed": "2025-06-01T12:00:00"},
    ...
  ]
}
```

### Pattern Detector
- **GET** `/ask/patterns`
- **Description:** Shows top tags and sources across the knowledge base.
- **Response Example:**
```json
{
  "top_tags": [["ai", 3], ["science", 2]],
  "top_sources": [["source1", 2], ["source2", 1]]
}
```

### Dashboard UI
- **GET** `/ask/html`
- **Description:** Interactive dashboard for all cognitive features. Use your browser to access and explore.

---

## 📥 Ingestion API (CLI/Scripted)

Atlas ingestion is typically run via CLI, but can be

*[truncated — see source for full prompt]*