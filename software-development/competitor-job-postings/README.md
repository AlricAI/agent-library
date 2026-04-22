# Competitor Job Postings

> ## Purpose
Monitor competitor career pages for new job postings. What they hire reveals what they're building next — a backend ML engineer means recom

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Competitor Job Postings

## Purpose
Monitor competitor career pages for new job postings. What they hire reveals what they're building next — a backend ML engineer means recommendation features, a CarPlay developer means vehicle integration, a "Head of Partnerships" means B2B push. Cheapest competitive intelligence there is.

## When to Use
- Scheduled: weekly on Wednesday at 7 AM ET (job postings don't change daily)
- On-demand: before strategic planning sessions

## Companies
- **DirtSync** — trail app competitors
- **Links Choice / Golf Ball Nut** — golf ball competitors

## Competitors to Monitor

### Trail / Outdoor Apps
1. **OnX** (onxmaps.com/careers) — Hunt, Offroad, Backcountry
2. **AllTrails** (alltrails.com/careers)
3. **GAIA GPS / Outside Inc** (outsideinc.com/careers)
4. **Trails Offroad** (small — check LinkedIn)
5. **Komoot** (komoot.com/jobs)
6. **CalTopo** (small — check LinkedIn)

### Golf Ball Competitors
7. **Lost Golf Balls** (lostgolfballs.com — check LinkedIn/Indeed)
8. **Golf Ball Planet** (LinkedIn/Indeed)
9. **Vice Golf** (vicegolf.com/careers)
10. **Acushnet / Titleist** (acushnetholdingscorp.com/careers) — the upstream giant

## Job Categories to Flag
- **Engineering — Mobile/iOS/Android**: building or improving their app
- **Engineering — ML/AI/Data**: recommendations, personalization, automation
- **Engineering — Maps/GIS/Spatial**: improving their mapping (direct DirtSync competitor move)
- **Product Manager**: new product lines coming
- **Head of Partnerships / BD**: B2B push, likely trail system or brand deals
- **Marketing / Growth**: scaling user acquisition
- **Supply Chain / Procurement**: (golf competitors) expanding sourcing
- **Content / Community**: building moat through user content

## Execution Steps

### Step 1: Scrape Career Pages
For each competitor:
- Check careers page for current openings
- Check LinkedIn "Jobs" filtered by company
- Check Indeed/Glassdoor for additional postings

### Step 2: Compare to Prev

*[truncated — see source for full prompt]*