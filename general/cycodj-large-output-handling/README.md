# Cycodj Large Output Handling

> ## The Pain 😫

**Current State:**
When analyzing longer time periods, outputs get massive and unusable:

**What I tried today:**
```bash
cycodj journ

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TODO: cycodj - Better Handling of Large Outputs

## The Pain 😫

**Current State:**
When analyzing longer time periods, outputs get massive and unusable:

**What I tried today:**
```bash
cycodj journal --last-days 9
```

**What happened:**
```
Output: [100,000 character limit reached]
... truncated ...
[59,155 lines remaining]
```

**The Problems:**
- **Truncation:** Lost most of the journal mid-week
- **No warning:** Tool didn't tell me output would be too large
- **No options:** Can't ask for summary-only or paginated output
- **Export also huge:** Exporting 9 days creates 1.5MB markdown file
- **Unusable for long periods:** Can't analyze a month or year
- **Terminal overload:** Huge outputs freeze/crash terminal

**Interesting discovery:** Different commands naturally have different detail levels!
- `list` shows minimal preview (1 message)
- `journal` shows summary preview (3 messages)
- `show` shows full detail (all messages)
- `stats` shows just numbers
- `branches` shows structure only

**But there's no way to control this across commands!**

**Real-world frustration:**
Wanted to analyze Dec 14-22 (9 days):
- Journal output hit my 100K char limit
- Couldn't see most days
- Had to do day-by-day queries instead
- Lost the "big picture" view

**For a month? Forget it.** Would be 300K+ characters.

---

## The Cure 💊

**What I Want:**
Smart handling of large outputs with multiple options:

### Option 1: Summary Mode
```bash
cycodj journal --last-days 30 --summary
```

**Output:**
```
Month Summary: December 2025

Week 1 (Dec 1-7):
  45 conversations | 5,200 messages | 8 branches
  Top topics: Testing framework (15 convs), Documentation (12 convs)
  
Week 2 (Dec 8-14):
  147 conversations | 18,000 messages | 30 branches
  Top topics: cycodgr implementation (50 convs), Debugging (35 convs)
  
Week 3 (Dec 15-21):
  450 conversations | 30,000 messages | 90 branches
  Top topics: Book summaries (100 convs), CDR project (240 convs)
  
Week 4 (Dec 22-28):
  50 convers

*[truncated — see source for full prompt]*