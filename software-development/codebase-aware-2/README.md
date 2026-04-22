# Codebase Aware

> ## Purpose
Load full architecture context before any code task. This is a **meta-skill** that other skills depend on. It ensures agents understand the

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Codebase Aware

## Purpose
Load full architecture context before any code task. This is a **meta-skill** that other skills depend on. It ensures agents understand the codebase before they start changing things.

## When to Use
- **Always.** This skill should be invoked (or its context injected) before any code task.
- It is a prerequisite for: [[agents/skills/visual-bug-fix.md]], [[agents/skills/plan-then-code.md]], [[agents/skills/code-review.md]]

## Context Files to Load

For each company, load from vault:

### 1. Company Profile (required)
- `vault/companies/{company}.md` -- tech stack, architecture, key files, current status
- This tells the agent: what framework, what language, what patterns, where files live

### 2. Known Issues (required)
- Check the "Blockers" and "Opportunities" sections of the company profile
- Avoid re-introducing known bugs or conflicting with in-progress work

### 3. Recent PRs (recommended)
- Last 5 merged PRs from the company's GitHub repo
- Command: `gh pr list --repo golfballnut/{repo} --state merged --limit 5`
- This shows: recent coding patterns, active areas of the codebase, naming conventions

### 4. Relevant Decision Logs (if applicable)
- Check `vault/decisions/` for any decisions related to the task
- Especially important for architectural decisions that constrain implementation choices

### 5. Related Competitor Intelligence (if applicable)
- If the task is feature development, check `vault/competitors/` for competitive context
- Example: building offline maps for DirtSync? Check [[competitors/onx.md]] for how OnX does it

## Company-to-Repo Mapping

| Company Slug | Repo | Framework | Key Directories |
|-------------|------|-----------|-----------------|
| `dirtsync` | `golfballnut/DirtSync` | React Native / Vercel | TBD -- needs architecture audit |
| `mcmforge` | `golfballnut/mcmforge` | Next.js + Supabase + Vercel | `app/`, `supabase/`, `lib/`, `vault/` |
| `linkschoice` | N/A (Shopify) | Liquid templates | Sho

*[truncated — see source for full prompt]*