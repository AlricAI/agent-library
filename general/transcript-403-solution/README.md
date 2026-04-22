# TRANSCRIPT 403 SOLUTION

> ## Problem Statement
When attempting to fetch transcripts from nytimes.com for podcasts like 'Hard Fork' and 'The Ezra Klein Show', the system encount

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 403 Forbidden Error Solutions for Podcast Transcripts

## Problem Statement
When attempting to fetch transcripts from nytimes.com for podcasts like 'Hard Fork' and 'The Ezra Klein Show', the system encounters 403 Forbidden errors that prevent transcript extraction.

## Root Causes
1. **User Agent Detection**: NYTimes blocks automated scraping attempts
2. **Rate Limiting**: Too many requests trigger blocking
3. **Paywall Protection**: Content requires authentication
4. **Anti-Bot Measures**: Advanced detection systems

## Solutions Implemented

### 1. Specialized NYTimes Handler (`nytimes_transcript_handler.py`)
- **Enhanced User Agents**: Modern browser signatures specifically for news sites
- **Realistic Headers**: Complete header simulation including security headers
- **Alternative Sources**: Multiple fallback strategies:
  - Rev.com transcript searches
  - Specialized podcast transcript sites
  - Listen Notes API integration
  - Google cache retrieval

### 2. Enhanced Transcript Orchestrator Integration
- Added NYTimes handler as Method 6 in the transcript discovery pipeline
- Automatic detection of NYTimes podcasts (Hard Fork, Ezra Klein, The Daily)
- Graceful fallback with clear error reporting
- Database tracking of unavailable transcripts with reasons

### 3. Database Schema Enhancement
- Added `transcript_status` field to track availability
- Added `transcript_error` field to record specific error reasons
- Prevents repeated failed attempts on known unavailable content

## Usage

### Automatic Integration
The system now automatically handles 403 errors for NYTimes podcasts:

```python
from transcript_orchestrator import find_transcript

# This will now handle 403 errors gracefully
transcript = find_transcript("Hard Fork", "Episode Title")
```

### Manual Testing
```bash
python3 nytimes_transcript_handler.py
```

### Database Status Check
```sql
SELECT podcast_name, episode_title, transcript_status, transcript_error
FROM episodes
WHERE transcript_status = 

*[truncated — see source for full prompt]*