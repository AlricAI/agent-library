# OOS LOG STREAM SPECIFICATION

> ## Universal Event Format

```
timestamp|event_type|content_type|source|item_id|data
```

### Field Definitions

#### timestamp (ISO 8601 UTC)
- Forma

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Log-Stream Event Format Specification

## Universal Event Format

```
timestamp|event_type|content_type|source|item_id|data
```

### Field Definitions

#### timestamp (ISO 8601 UTC)
- Format: `2025-09-29T01:08:38.246Z`
- Precision: Millisecond precision
- Timezone: Always UTC
- Purpose: Exact event timing for analytics and debugging

#### event_type (ENUM)
Core lifecycle events:
- `DISCOVER` - New content discovered
- `PROCESS` - Processing started
- `COMPLETE` - Processing successful
- `FAIL` - Processing failed
- `SKIP` - Content skipped (duplicate, invalid, etc.)
- `RETRY` - Retrying failed processing
- `METRICS` - System metrics and statistics

#### content_type (ENUM)
All supported OOS content types:
- `podcast` - Podcast episodes and transcripts
- `article` - Web articles and documents
- `email` - Email messages and attachments
- `video` - Video content and metadata
- `documentation` - Technical documentation
- `url` - Generic URL processing
- `audio` - Audio file processing

#### source (STRING)
Source system or feed identifier:
- Podcasts: `Asianometry`, `This American Life`, `Lex Fridman`, etc.
- Articles: `TechCrunch`, `Stratechery`, `Hacker News`, etc.
- Emails: `gmail`, `protonmail`, etc.
- Videos: `YouTube`, `Vimeo`, etc.
- Generic: `web_crawler`, `rss_feed`, `api`

#### item_id (STRING)
Unique identifier for content item:
- Format: `{source}_{unique_hash}` or `{source}_{timestamp}`
- Purpose: Track content through processing pipeline
- Example: `Asianometry_20250929_010838`, `TechCrunch_abc123`

#### data (JSON string)
Flexible payload with event-specific data:
- Discovery events: URLs, metadata
- Processing events: Status, progress
- Completion events: Results, file paths
- Failure events: Error details, retry info

## Event Examples

### Podcast Processing Pipeline

```
# Episode discovery
2025-09-29T01:08:38.246Z|DISCOVER|podcast|Asianometry|Asianometry_20250929_010838|{"url":"https://feeds.simplecast.com/ABC123","title":"Episode 123: AI Revol

*[truncated — see source for full prompt]*