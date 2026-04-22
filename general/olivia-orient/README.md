# Olivia Orient

> ## When To Use

Use this when a session needs full-project orientation rather than the lighter task-based orientation described in `AGENTS.md`.

Typic

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Olivia Session Orientation

## When To Use

Use this when a session needs full-project orientation rather than the lighter task-based orientation described in `AGENTS.md`.

Typical cases:
- starting a major planning session
- recovering after a long context gap
- unsure which milestone or horizon is active
- needing a broad project-state summary before deciding the next action

## Goal

Orient to the current project state, assess milestone progress, surface active assumptions and open questions, and recommend the single highest-value next action.

## Steps

### 1. Read the core docs in order

Read each file completely:

1. `docs/vision/product-vision.md`
2. `docs/vision/product-ethos.md`
3. `docs/strategy/agentic-development-principles.md`
4. `docs/glossary.md`
5. `docs/roadmap/roadmap.md`
6. `docs/roadmap/milestones.md`
7. `docs/learnings/decision-history.md`
8. `docs/learnings/assumptions-log.md`
9. `docs/learnings/learnings-log.md`

### 2. Assess milestone status

- Compare the required artifacts for M0 through the current active milestone in `docs/roadmap/milestones.md` against the current repo state.
- Identify which milestone is currently active.
- Check whether the exit criteria for the active milestone appear satisfied from the docs alone.

### 3. Produce a structured orientation summary

Use this structure:

#### Project Summary
- One or two sentences on what Olivia is and its current phase.

#### Current Milestone
- State the active milestone, its objective, and which required artifacts are present versus missing.

#### Milestone Gate Status
- For each milestone from M0 through the current horizon's active milestone, mark `Complete`, `In Progress`, or `Not Started` with a one-line reason.

#### Active Assumptions
- List all assumptions from `docs/learnings/assumptions-log.md` with their confidence.
- Clearly flag any `low` confidence assumptions.

#### Latest Decisions
- List the three most recent decisions from `docs/learnings/decision-history.md

*[truncated — see source for full prompt]*