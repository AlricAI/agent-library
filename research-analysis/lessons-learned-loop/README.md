# Lessons Learned Loop

> > Last updated: April 9, 2026
> Used by: Every MCM Forge agent — specialists, routine agents, QA, Critique, Ship, CEO/COO, Factory Analyst
> Origin: S

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Lessons Learned Loop

> Last updated: April 9, 2026
> Used by: Every MCM Forge agent — specialists, routine agents, QA, Critique, Ship, CEO/COO, Factory Analyst
> Origin: Session of April 9, 2026 — closing the silent-failure gap where agents start cold every heartbeat and repeat bugs the factory already knows how to fix (`feedback_agent_learning_gap.md`, `project_auto_learning_loop_needed.md`)

---

## Goal

Make the factory's hard-won knowledge persist across agent restarts. Every agent keeps a `LESSONS.md` file in its own directory. On wake, the agent reads it and applies relevant lessons before touching code. On exit, the agent appends any non-trivial bugs it encountered this run — what broke, what it tried, whether the fix worked, and why. The next wake starts smarter than the last.

This skill is the enforcement contract. It is the reason Anvil Loop's Record phase exists. Without it, every strike re-learns what the factory already knew.

## Definition of Done

**YOU ARE NOT DONE UNTIL ALL OF THIS IS TRUE:**

1. `LESSONS.md` exists in your agent directory (create with header if missing)
2. You read `LESSONS.md` **before** writing any code or running any tool that changes state
3. If a bug matches a recorded lesson, you try the recorded fix first
4. You appended one entry per non-trivial bug encountered this run, using the format below
5. Newest entries are at the top of the file
6. The `LESSONS.md` change is committed with the rest of your work on the same branch
7. You did not delete or edit older entries — append-only
8. If the file is over 50 entries, the oldest are rolled into `LESSONS_ARCHIVE.md` (Factory Analyst handles this weekly — you do not)

**If any item above is false, you are NOT done. This is enforced by HEARTBEAT.md step 1 and the HEARTBEAT.md final step.**

## Pre-Made Decisions

**DO NOT ask about these. They are already decided.**

| Decision | Answer |
|----------|--------|
| Where LESSONS.md lives | Your own agent directory — the sa

*[truncated — see source for full prompt]*