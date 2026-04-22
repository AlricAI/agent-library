# Google Trends Pulse

> ## Purpose
Track daily search volume trends for keywords relevant to all 5 companies. Detect rising interest, seasonal patterns, and emerging opportun

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Google Trends Pulse

## Purpose
Track daily search volume trends for keywords relevant to all 5 companies. Detect rising interest, seasonal patterns, and emerging opportunities before competitors notice.

## When to Use
- Scheduled: daily at 5 AM ET (after price monitor and app store monitor)
- On-demand: before marketing decisions, content planning, or new product launches

## Companies
- **DirtSync** — trail/outdoor search trends
- **Links Choice** — recycled golf ball wholesale trends
- **Golf Ball Nut** — recycled golf ball retail trends
- **Hot Golf Brands** — bulk golf ball trends
- **MCM Forge** — AI ops/automation trends

## Keywords to Track

### DirtSync Keywords
- trail navigation app
- ATV trail maps
- UTV trail app
- off-road GPS
- Hatfield McCoy trails
- dirt bike trail finder
- offline trail maps
- side by side trail maps
- OHV trails near me

### Golf Ball Keywords (Links Choice / Golf Ball Nut / Hot Golf Brands)
- recycled golf balls
- used golf balls
- bulk golf balls
- cheap golf balls
- golf ball deals
- Pro V1 used
- refurbished golf balls
- lake balls golf
- golf balls wholesale

### MCM Forge Keywords
- AI automation platform
- AI agent orchestration
- autonomous AI agents
- Claude API
- AI ops

## Execution Steps

### Step 1: Query Google Trends
For each keyword group:
- Pull interest-over-time data (last 7 days vs previous 7 days)
- Pull related queries (rising and top)
- Pull geographic breakdown (US states)

### Step 2: Detect Signals
- **Breakout**: keyword jumped 100%+ week-over-week → urgent opportunity
- **Rising**: keyword up 20-99% → emerging trend
- **Declining**: keyword down 20%+ → market shift or seasonal
- **Seasonal**: compare to same week last year

### Step 3: Cross-Reference
- Rising trail keyword + DirtSync coverage gap = content/feature opportunity
- Rising golf ball keyword + our inventory = marketing push
- Competitor name trending = something happened (press, outage, launch)

### Step 4: Generate Report
Post to

*[truncated — see source for full prompt]*