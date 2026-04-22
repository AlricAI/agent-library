# Golden Feature

> > Last updated: April 1, 2026
> Used by: MCM Forge COO, DirtSync COO, all engineers
> Origin: Session 69 — Steve's Why/How/What formula applied to Dir

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Golden Feature

> Last updated: April 1, 2026
> Used by: MCM Forge COO, DirtSync COO, all engineers
> Origin: Session 69 — Steve's Why/How/What formula applied to DirtSync navigation

---

## Goal
Turn any rider need (a "mini-why") into a fully tested, shippable feature using the Why → How → What loop. The Why defines the rider's need. The How maps the workflow and tech. The What is a test contract — unit, integration, and field tests that MUST all pass before shipping. Gold = every row in the What passes. This skill replaces "tell Claude how to build stuff" with "give Claude the Why and let it prove the What."

## Definition of Done
**YOU ARE NOT DONE UNTIL ALL OF THIS IS TRUE:**
1. Mini-Why is stated in one sentence from the rider's perspective
2. How workflow diagram + tech stack table exist
3. What test matrix has unit, integration, AND field test rows
4. All unit tests pass
5. All integration tests pass
6. Field test matrix presented to Steve with pass/fail columns
7. Steve runs field test and marks all rows pass
8. PR merged to master
9. Gotchas from this run appended to this skill

**If any item is false, you are NOT done. Loop back.**

## Pre-Made Decisions
**DO NOT ask about these. They are already decided.**

| Decision | Answer |
|----------|--------|
| Planning tool | superpowers:writing-plans |
| Execution tool | superpowers:subagent-driven-development |
| Test approach | TDD — What (tests) defined before How (code) is built |
| Branch strategy | Feature branch → PR → Steve approves → merge |
| Voice of the Why | Always from rider's perspective, never technical |
| Gold criteria | 100% of What test matrix rows pass |
| Failure response | Diagnose → fix → re-test (never ship with fails) |

## Execution Flow

### Phase 1: WHY — What does the rider need?
- State the Big Why (product purpose) in one sentence
- Break into Mini-Whys (individual rider wants)
- Each mini-why = one sentence, rider's voice: "Where are my buddies right now?"
- Prioritize:

*[truncated — see source for full prompt]*