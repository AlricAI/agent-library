# DATA DICTIONARY

> This document defines every data field in Lumineer — from the source Coursera dataset to the PostgreSQL schema and Qdrant vector payload.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Data Dictionary

This document defines every data field in Lumineer — from the source Coursera dataset to the PostgreSQL schema and Qdrant vector payload.

---

## 1. Coursera Dataset (Source)

**File:** `data/raw/coursera.parquet` — 6,645 rows, 11.4 MB

| Column | Type | Null rate | Notes |
|--------|------|-----------|-------|
| `Title` | string | 0% | Course name |
| `Description` | string | 0% | Full marketing description. Avg 3,198 chars, max 32,804 chars |
| `Skills` | string (JSON list) | 29% | Tags like `["Python", "Machine Learning"]`. Empty for 1,954 courses |
| `Level` | string | 12% | `"Beginner"` · `"Intermediate"` · `"Advanced"` · missing (778 courses) |
| `Organization` | string | 0% | Provider name e.g. `"Stanford University"` |
| `Rating` | string | 0% | Numeric string `"4.8"` — converted to `float` at ingestion |
| `Enrolled` | string | 0% | Numeric string `"1234567"` — converted to `int` at ingestion |
| `Modules/Courses` | string | varies | Course structure summary |
| `Schedule` | string | varies | Duration e.g. `"Approximately 3 months at 10 hours/week"` |
| `URL` | string | 0% | Full Coursera URL |
| `Instructor` | string | varies | Instructor name(s) |

**Data quality issues handled at ingestion:**
- `Skills` null (29%) → GPT-4o-mini infers skills from `Description`
- `Level` format varies (`"Beginner level"`, `"Beginner"`) → normalized to canonical value
- `Rating` / `Enrolled` stored as strings → cast at ingestion

---

## 2. Qdrant Vector Payload

After ingestion, each course is stored as a Qdrant point. The payload contains the original data plus the LLM-generated `search_text`.

| Field | Type | Indexed | Description |
|-------|------|---------|-------------|
| `title` | string | — | Course title (display) |
| `description` | string | — | Original full description (LLM context) |
| `skills` | string[] | ✅ `match_any` | Skill tags — used for filtering and embedding |
| `level` | string \| null | ✅ exact match | `"Beginner"` · `"Intermed

*[truncated — see source for full prompt]*