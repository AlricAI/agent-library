# Anvil Loop

> > Last updated: April 9, 2026
> Used by: All MCM Forge specialist agents (Feature Builder, iOS Builder, Map Rendering Expert, Nav HUD Polish Expert, E

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Anvil Loop

> Last updated: April 9, 2026
> Used by: All MCM Forge specialist agents (Feature Builder, iOS Builder, Map Rendering Expert, Nav HUD Polish Expert, Explore UX Expert, Test Runner, Critique Agent, QA Rider, Ship Engineer)
> Origin: Session of April 9, 2026 — naming and formalizing the specialist-team learning pattern that replaces Ralph Loop

---

## Goal

Ship features that are **measurably done** by striking the same spec from multiple angles until every test row is green and every pixel matches the Gold Star. This skill is the named, documented version of the pattern the factory already runs — it exists so agents have one shared vocabulary for how work flows from an issue to a shipped PR.

The anvil is where metal becomes the thing. Each "strike" is a specialist agent run against a fixed spec. Quality is measured after every strike. The work is done when the shape matches the spec — not when the agent decides it looks fine.

## Definition of Done

**YOU ARE NOT DONE UNTIL ALL OF THIS IS TRUE:**

1. Gold Star test matrix existed **before** the first strike (Spec phase)
2. A specialist agent executed against the spec on a clean feature branch (Strike phase)
3. XCUITest suite runs and reports pass/fail per row — no subjective grading (Measure phase)
4. Simulator screenshot captured and diffed against the Gold Star reference (Measure phase)
5. Every failed row is reflected as a new entry in the agent's `LESSONS.md` (Record phase)
6. Factory Analyst has visibility into the run in the next 7 AM sweep (Reflect phase)
7. Loop continues until every Gold Star row is green AND pixel diff is under threshold
8. Issue is marked `in_review` with a comment linking to the test report and screenshot
9. No row, no pixel, no rider-visible behavior is "close enough" — close enough is a fail

**If any item above is false, you are NOT done. Loop back to the phase that broke.**

## Pre-Made Decisions

**DO NOT ask about these. They are already decided.**

| Decision

*[truncated — see source for full prompt]*