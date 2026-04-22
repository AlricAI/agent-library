# Reasoning Model Prompting

> > Extended-thinking models have different token economics and cognitive patterns.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Reasoning-Model Prompting

> Extended-thinking models have different token economics and cognitive patterns. Let them think.

Reasoning models (Claude Opus 4 with extended thinking, o3/o3-mini) operate at a different cost and latency boundary than standard models. They trade 2-10x latency and 3-5x token cost for dramatically higher first-pass quality on hard problems. This requires a different prompting discipline: less scaffolding, more constraints, explicit reasoning budgets.

## Core Principle: Don't Force Chain-of-Thought

**Anti-pattern:**
```
User: Find the bug in this code. Think step by step:
1. First, list the function signature
2. Then, check for off-by-one errors
3. Finally, test with edge cases
```

**Why it fails:** Reasoning models already think in steps internally. Forcing them to output your prescribed steps wastes tokens (your format) and prevents them from thinking in ways that work for them.

**Better pattern:**
```
User: Find the bug in this code. Focus on edge cases and off-by-one errors.
```

Let the model's internal reasoning find the right breakdown. Enable extended thinking (`reasoning_effort: "high"` or `thinking` mode), and it will explore multiple paths internally, then output a concise answer.

## The Reasoning Budget Knob

Reasoning models expose a cost/quality tradeoff as an explicit parameter:

| Parameter | Cost | Latency | Use Case |
|-----------|------|---------|----------|
| `reasoning_effort: "low"` | 1x base cost | 2-3 sec | "Double-check my math" |
| `reasoning_effort: "medium"` | 3x base cost | 4-8 sec | "Find the subtle bug" |
| `reasoning_effort: "high"` | 5x+ base cost | 8-30 sec | "Prove this is correct" or "Redesign this system" |

**When to allocate:** Don't enable high reasoning by default. Allocate reasoning effort proportional to task difficulty and cost-of-failure:

- **Bug fix?** Medium (high effort wastes time on obvious bugs; low effort misses edge cases).
- **Security review?** High (cost of missing a vulnerabi

*[truncated — see source for full prompt]*