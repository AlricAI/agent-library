# MASTER SKILL TEMPLATE

> > Last updated: March 23, 2026
> Used by: MCM Forge COO, DirtSync COO, all engineers
> Source: Anthropic's official skill guide + video breakdown + Di

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCM Forge — Master Skill Template v1.1 (GOLD STANDARD)
> Last updated: March 23, 2026
> Used by: MCM Forge COO, DirtSync COO, all engineers
> Source: Anthropic's official skill guide + video breakdown + DirtSync 1-04 cherry-picks
> This is the GOLD STANDARD. All skills across all companies follow this format.

---

## How to Use This Template
1. Copy this structure when creating any new skill
2. Follow the principles below — they matter more than the format
3. After each skill runs, improve it (add gotchas, refine scripts, update data)
4. When this template itself improves, all future skills benefit
5. Run `/enhance-skill [skill-name]` to upgrade any existing skill to this standard

---

## Principles (Read This First)

### 1. Skills Shift Claude's Distribution — Don't Restate Defaults
A skill should push Claude AWAY from its default high-probability output. If Claude would already do it without the skill, don't put it in the skill. Encode YOUR lived experience, YOUR business context, things Claude doesn't know from training data.

**Bad:** "Search the web for competitor prices and compare them"
**Good:** "Nike balls at $0.15 and bulk at $0.10 are our floor. Anything below that is a red flag — either counterfeit or water-damaged inventory. We learned this after the Tampa batch in Q3."

### 2. Goal-Oriented, Not Step-by-Step (Don't Railroad)
Tell Claude WHAT you want and WHY, not HOW to do every step. Rigid recipes collapse Claude's solution space and give identical outputs every run.

**Bad (railroading):**
```
Step 1: Go to lostgolfballs.com
Step 2: Search for "Pro V1 Mint"
Step 3: Copy the price
Step 4: Compare to yesterday's price
```

**Good (goal-oriented):**
```
Find pricing opportunities we're missing across our competitor set.
Context: our current prices are in the attached sheet.
Focus on gaps > 15% — those are actionable.
```

### 3. Gotchas Are the Most Valuable Section
Like training a new employee — don't just tell them what to do, tell them what to wa

*[truncated — see source for full prompt]*