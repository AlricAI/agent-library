# Multi Model Routing

> > Use the cheapest model that can do the job.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Model Routing

> Use the cheapest model that can do the job. Escalate only when needed.

## The Problem

Using a frontier model for every task wastes money and time. Using a weak model for hard tasks wastes your time fixing its output. The optimal strategy routes tasks to the right capability tier.

## The Pattern

### Three-Tier Routing

| Tier | Use For | Examples |
|------|---------|---------|
| **Fast** (Haiku, GPT-5.4 mini, Flash) | Simple edits, formatting, config changes, file renames, quick lookups | Fix a typo, rename a variable, update a dependency version |
| **Standard** (Sonnet, GPT-5.4, Pro) | Implementation, debugging, refactoring, test writing | Build a feature, fix a bug, write tests, code review |
| **Deep** (Opus, GPT-5-Codex, Deep Research) | Architecture design, cross-system impact, complex debugging, planning | Design an API, analyze a race condition, plan a migration |

### Routing Heuristics

**Route to Fast when:**
- The task is mechanical (formatting, renaming, moving)
- The output is easily verified (linting, type errors)
- The context is small (<5 files)
- You could do it yourself in 2 minutes

**Route to Standard when:**
- The task requires understanding business logic
- Multiple files need coordinated changes
- Tests need to be written or fixed
- The output needs code review

**Route to Deep when:**
- The decision has cross-repo impact
- Multiple valid approaches exist and the tradeoffs matter
- The problem requires reasoning across >10 files
- You're planning, not implementing

### Cost Math

| Tier | Relative Cost | Speed |
|------|--------------|-------|
| Fast | 1x | Instant |
| Standard | 5-10x | Fast |
| Deep | 20-50x | Slow |

A typical day might be: 70% Fast, 25% Standard, 5% Deep.

## Tool-Specific Mapping

| Tier | Claude | OpenAI | Google |
|------|--------|--------|--------|
| Fast | Haiku 4.5 | GPT-5.4 mini | Flash 2.5 |
| Standard | Sonnet 4.6 | GPT-5.4 | Pro 2.5 |
| Deep | Opus 4.6 | GPT-5-Codex | Deep Research |


*[truncated — see source for full prompt]*