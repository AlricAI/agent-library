# README

> Daily agent that monitors curated AI researcher Twitter accounts, analyzes discussions, generates a markdown report + audio podcast, and broadcasts to subscribers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Twitter Daily Agent

Daily agent that monitors curated AI researcher Twitter accounts, analyzes discussions, generates a markdown report + audio podcast, and broadcasts to subscribers.

## SMS Commands

| Command | Description | Access |
|---------|-------------|--------|
| `AIT` / `AI TWITTER` | Get latest report + podcast | All users |
| `AIT SUB` | Subscribe to daily digest | Registered users |
| `AIT UNSUB` | Unsubscribe | Subscribers |
| `AIT ADD @handle` | Add account to sources | Admin only |
| `AIT LIST` | List all source accounts | Admin only |
| `AIT RUN` | Run the daily agent manually | Admin only |

## Architecture

```
sms-bot/agents/ai-twitter-daily/
├── index.ts              # Main orchestrator
├── twitter-fetcher.ts    # Fetch tweets via search API workaround
├── content-analyzer.ts   # AI analysis (topic grouping, insights)
└── README.md             # This file
```

## Daily Flow

1. **Fetch**: Load active handles from `content_sources` table, build search queries
2. **Filter**: Keep tweets from last 24 hours only
3. **Analyze**: Group by topic, extract key insights (OpenAI)
4. **Report**: Generate markdown → store via `storeAgentReport()`
5. **Podcast**: Generate script (OpenAI) → synthesize (ElevenLabs) → upload to storage
6. **Store**: Upsert episode to `episodes` table, covered tweets to `covered_content`
7. **Broadcast**: (Future) Send to subscribers via agent subscriptions

## Twitter API Workaround

**Problem**: Twitter free tier does NOT support reading timelines (requires $200/mo Basic).

**Solution**: Use `searchTweets("from:handle1 OR from:handle2 OR ...")` — search API works on free tier. The agent dynamically builds queries from the `content_sources` table, batching by 10 handles per query.

## Database Schema

### `content_sources` (universal source registry)
```sql
CREATE TABLE content_sources (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  agent_slug text NOT NULL,        -- 'ai-twitter-daily'
  source_type text NOT NULL,  

*[truncated — see source for full prompt]*