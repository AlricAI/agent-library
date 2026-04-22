# Issue Prep Rubric

> > Last updated: April 20, 2026
> Applies to: anyone filing a `forge.issue` before it ships to an agent
> Enforced by: CEO review before `status` trans

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Issue Prep Rubric (10-Item Dispatch Checklist)

> Last updated: April 20, 2026
> Applies to: anyone filing a `forge.issue` before it ships to an agent
> Enforced by: CEO review before `status` transitions from `todo` → `in_progress` with an assignee

---

## Goal

Make every issue **ready to ship before it's dispatched**. An agent shouldn't have to infer, search, or ask. Tight spec = A+. Loose spec = B+. Loose spec with no file paths = agent spirals and burns tokens.

## The 10 items

Every issue MUST pass all 10 before dispatch:

1. **Acceptance criteria** — numbered list, measurable (`grep -c X == 0`, `xcodebuild exit 0`, `assertion spec X passes`). No "verify in the field" without a specific harness.

2. **File paths (exact)** — every file the agent will create or modify, full path. Never "find the right place for this."

3. **Out-of-scope list** — what NOT to touch (other routes, other services, other agents' files, refactor opportunities).

4. **Assigned specialist(s)** — primary agent name + adapter type. If team work, list each specialist and what each is responsible for. Match specialist to task:
   - **Feature Builder** — general dashboard/app features, Swift or TS
   - **Forge Builder** — MCMForge orchestrator, dashboard TS, infrastructure
   - **iOS Builder** — iOS-specific compilation & Xcode gymnastics
   - **Map Rendering Expert** — MapLibre styles, tile logic, map rendering
   - **Nav HUD Polish Expert** — TurnCardView, ETA, maneuver UI
   - **Explore UX Expert** — pre-nav trail discovery, POI, onboarding
   - **DirtSync Trail Data Engineer** — OSM / Valhalla / trail detection
   - **Test Writer / Test Runner** — XCUITest authoring and execution
   - **QA Recorder** — sim harness, screenshot/video capture
   - **Critique Agent / Visual Judge** — compare to Gold Star reference
   - **Solutions Architect** — design before code for non-trivial changes

5. **Agent team trigger** — if the task crosses domains (code + test + UI), assign a team and 

*[truncated — see source for full prompt]*