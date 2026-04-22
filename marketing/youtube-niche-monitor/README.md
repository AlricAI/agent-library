# Youtube Niche Monitor

> ## Purpose
Track new videos from golf, overlanding, UTV, and trail riding YouTube channels. Detect trending topics, view velocity, and content gaps we

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: YouTube Niche Monitor

## Purpose
Track new videos from golf, overlanding, UTV, and trail riding YouTube channels. Detect trending topics, view velocity, and content gaps we can exploit. Feeds content strategy for DirtSync marketing and golf brand awareness.

## When to Use
- Scheduled: daily at 7 AM ET
- On-demand: before content planning sessions

## Companies
- **DirtSync** — trail/UTV/overlanding content trends
- **Links Choice** — golf ball review and deal content
- **Golf Ball Nut** — golf ball comparison content
- **Hot Golf Brands** — bulk golf ball content opportunities

## Channels to Monitor

### Trail / Off-Road / UTV
1. TrailsOffroad (official channel)
2. Hatfield-McCoy Trails (official)
3. UTV Driver
4. Dirt Trax TV
5. SuperATV
6. SXS Guys
7. Search: "UTV trail riding" — top 5 new videos this week
8. Search: "ATV trail app" — any new content

### Golf / Golf Balls
9. Rick Shiels Golf
10. Good Good
11. Golf Sidekick
12. MyGolfSpy
13. Search: "recycled golf balls" — any new content
14. Search: "used golf balls review" — any new content
15. Search: "golf ball comparison" — top 5 new videos this week

### Overlanding / Outdoor
16. Expedition Overland
17. Lifestyle Overland
18. Search: "off-road navigation app" — any new content

## Data Points Per Video
- **Title** and **description** (first 200 chars)
- **Views** and **view velocity** (views per day since publish)
- **Publish date**
- **Like/comment ratio** (engagement signal)
- **Tags/keywords** used
- **Duration** (short-form vs long-form trend)

## Execution Steps

### Step 1: Check Monitored Channels
For each channel:
- Fetch last 5 videos
- Check if any are new since last scan
- Extract data points

### Step 2: Run Keyword Searches
For each search query:
- YouTube search, sort by upload date (last 7 days)
- Top 5 results per query
- Flag any video mentioning DirtSync competitors or our golf brands

### Step 3: Detect Signals
- **Viral**: video got 10x the channel's average views → trending t

*[truncated — see source for full prompt]*