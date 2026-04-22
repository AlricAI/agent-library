# GOOGLE SEARCH FALLBACK

> ## 🎯 Mission Statement
**"NO content is EVER lost. If Google can find it, Atlas will get it."**

The Universal Google Search Fallback system is the u

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Universal Google Search Fallback System

## 🎯 Mission Statement
**"NO content is EVER lost. If Google can find it, Atlas will get it."**

The Universal Google Search Fallback system is the ultimate safety net for Atlas content ingestion. When all traditional methods fail, this system uses Google Search to find alternative sources and ensures content is never truly lost.

## 🏗️ System Architecture

### Core Components

1. **GoogleSearchFallback** (`helpers/google_search_fallback.py`)
   - Main search engine with rate limiting and circuit breaker
   - Handles 8,000 daily queries (80% of 10k Google limit)
   - Exponential backoff and intelligent retry logic

2. **GoogleSearchQueue** (`helpers/google_search_queue.py`)
   - Database-backed persistent queue for search requests
   - Priority system: Urgent (1) > Normal (2) > Background (3)
   - Automatic retry scheduling with backoff

3. **GoogleSearchWorker** (`helpers/google_search_worker.py`)
   - Background worker processing queue at controlled rate
   - 1 search every 11 seconds to respect API limits
   - Graceful handling of rate limits and quota exhaustion

4. **GoogleSearchAnalytics** (`helpers/google_search_analytics.py`)
   - Comprehensive monitoring and analytics dashboard
   - Performance metrics, usage patterns, alerts
   - Daily reports and real-time status

5. **NuclearFallback** (`helpers/nuclear_fallback.py`)
   - Ultimate safety net that NEVER gives up
   - Persistent failure tracking and infinite retry logic
   - Human escalation after 30 failed attempts

### Integration Points

- **ArticleFetcher**: Enhanced with 4 new community paywall bypass strategies + Google fallback
- **Content Router**: Auto-fallback on ingestion failures
- **CSV Processing**: Google search for email titles and missing content
- **API Endpoints**: Real-time analytics and monitoring

## 🚀 Quick Start

### 1. Environment Setup
```bash
# Set Google API credentials in .env
GOOGLE_SEARCH_API_KEY=YOUR_GOOGLE_SEARCH_API_KEY_HERE
GO

*[truncated — see source for full prompt]*