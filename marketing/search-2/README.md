# Search

> ## Overview
The Genonaut search feature provides comprehensive search capabilities across content items (both regular and auto-generated) with support

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Search Feature Documentation

## Overview
The Genonaut search feature provides comprehensive search capabilities across content items (both regular and auto-generated) with support for literal phrase matching and search history tracking.

## Search Algorithm

### Query Parsing
The search parser (`genonaut/api/services/search_parser.py`) extracts two types of patterns from user queries:

1. **Quoted Phrases**: Text within double quotes is treated as a literal phrase
   - Example: `"my cat"` matches only items containing the exact phrase "my cat"
   - Supports escaped quotes within phrases: `"phrase with \"nested\" quotes"`

2. **Individual Words**: Text outside of quotes is treated as individual words
   - Example: `my cat` matches items containing either "my" OR "cat"

### Search Execution
- **Fields Searched**: Both `title` and `prompt` fields
- **Matching Logic**: All phrases and words must match (AND logic)
  - Each phrase must appear in either title or prompt
  - Each word must appear in either title or prompt
- **Database Implementation**: Uses PostgreSQL ILIKE for case-insensitive substring matching
- **Performance**: Leverages existing indexes on title and prompt fields

### Search Examples

```
Query: cat dog
Matches: Items with "cat" AND "dog" anywhere in title or prompt

Query: "black cat" dog
Matches: Items with the exact phrase "black cat" AND the word "dog"

Query: "my cat" "my dog"
Matches: Items with both phrases "my cat" AND "my dog"
```

## Search History

### Storage
- **Table**: `user_search_history`
- **Fields**: id, user_id, search_query (max 500 chars), created_at
- **Indexes**:
  - Primary: user_id
  - Composite: (user_id, created_at DESC) for efficient recent search queries

### Features
- **Automatic Recording**: Every search is automatically saved to history
- **No Deduplication**: All searches are recorded, including duplicates
- **Retention**: No automatic cleanup (infinite retention)
- **Privacy**: Search history is per-user and not sh

*[truncated — see source for full prompt]*