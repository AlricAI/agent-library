# ENGINEER PROMPT Wire 9 Skills

> ## Context
9 new skill specs have been drafted in `vault/agents/skills/`. They need to be registered in the dispatcher and scheduled in night-ops. Add

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Engineer Prompt: Wire 9 New Skills into Dispatcher + Fix Scheduler

## Context
9 new skill specs have been drafted in `vault/agents/skills/`. They need to be registered in the dispatcher and scheduled in night-ops. Additionally, the existing scheduler has bugs — most schedules have `next_run_at = NULL` which means they never fire.

## Task 1: Add new skills to VALID_SKILLS

**File:** `dispatcher/dispatcher.ts` line 133

Current:
```typescript
const VALID_SKILLS = new Set([
  "poi-research", "competitive-scan", "code-review", "visual-bug-fix",
  "plan-then-code", "tdd-workflow", "shipping-checklist", "codebase-aware",
  "feature-proposal", "daily-ops", "plan-reviewer", "ai-daily-intel", "social-intel",
]);
```

Add these 9 new skills:
```
"competitor-price-monitor", "app-store-monitor", "google-trends-pulse",
"trail-closure-monitor", "youtube-niche-monitor", "supplier-news-monitor",
"skill-gotchas-flywheel", "gmail-draft-outreach", "competitor-job-postings",
"system-health"
```

(Note: `system-health` is already in skill_schedule but missing from VALID_SKILLS.)

## Task 2: Update FALLBACK_ORCHESTRATOR_PROMPT

**File:** `dispatcher/dispatcher.ts` line 140

Add the new skills to the prompt so the Gemini orchestrator can classify tasks into them:
- competitor-price-monitor (competitor golf ball pricing)
- app-store-monitor (track competitor app updates/reviews)
- google-trends-pulse (search volume trends)
- trail-closure-monitor (forest service/BLM trail closures)
- youtube-niche-monitor (golf/trail YouTube content tracking)
- supplier-news-monitor (golf ball manufacturer news)
- skill-gotchas-flywheel (meta: improve other skills from failures)
- gmail-draft-outreach (create procurement email drafts)
- competitor-job-postings (competitor hiring signals)

## Task 3: Insert skill_schedule rows

Run this SQL migration (or apply via Supabase Dashboard):

```sql
-- Fix existing NULL next_run_at values (BUG: scheduler skips rows with NULL next_run_at)
UPDATE skill_schedule 

*[truncated — see source for full prompt]*