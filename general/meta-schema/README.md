# META SCHEMA

> Each library directory under `docs/{source-type}/{library}/` may contain a `_meta.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# _meta.yaml Schema

Each library directory under `docs/{source-type}/{library}/` may contain a `_meta.yaml` file
that describes the library, its documentation sources, and quality metadata.

## File Location

```
docs/
  llms-txt/
    slack/
      _meta.yaml    <-- per-library metadata
      ...
  github-scraped/
    tornado/
      _meta.yaml
      ...
  web-scraped/
    apple-developer-docs/
      _meta.yaml
      ...
```

## Schema

```yaml
# _meta.yaml schema - one per library in docs/{source-type}/{library}/
name: string           # library identifier (matches directory name)
primary_source: enum   # llms | github | web
sources:               # all sources fetched for this library
  - type: llms | github | web
    url: string        # source URL
    last_fetched: ISO8601 datetime
description: string    # human-readable description of the library
quality_score: int     # 0-100, computed by scripts/quality-check.py
```

## Field Descriptions

### `name`

**Type:** string
**Required:** yes

The library identifier. Must match the directory name exactly. Used as the canonical
identifier for cross-referencing in `index.yaml` and search indexes.

Example: `slack`, `tornado`, `apple-developer-docs`

### `primary_source`

**Type:** enum
**Required:** yes
**Values:** `llms` | `github` | `web`

The primary documentation source type:

| Value | Description |
|-------|-------------|
| `llms` | Fetched via `llms.txt` protocol from the library's official site |
| `github` | Scraped from a GitHub repository's docs folder |
| `web` | Scraped from a web URL via HTTP crawler |

When a library has multiple sources, `primary_source` indicates the most authoritative one.

### `sources`

**Type:** list of source objects
**Required:** yes
**Min length:** 1

Each source object has the following fields:

#### `sources[].type`

**Type:** enum (`llms` | `github` | `web`)

The source type for this entry. Matches the `primary_source` enum values.

#### `sources[].url`

**Type:** string (URL

*[truncated — see source for full prompt]*