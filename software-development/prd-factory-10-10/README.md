# Prd Factory 10 10

> ## Vision
Steve creates an issue on his phone. He walks away. He comes back to a thoroughly tested, feature-rich app ready to distribute to users via 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PRD: Factory 10/10 — Autonomous App Shipping

## Vision
Steve creates an issue on his phone. He walks away. He comes back to a thoroughly tested, feature-rich app ready to distribute to users via TestFlight. No debugging, no manual patches, no babysitting agents.

## Success Criteria
Steve can:
1. Create an issue with a one-line description
2. Walk away for 24 hours
3. Come back to an email with: screenshot proof, test results, PR link
4. Approve the PR
5. App auto-builds to TestFlight

## Current State: 1/10
- Plumbing exists (orchestrator, 14 agents, Mini, simulator)
- No agent has completed a full issue autonomously with screenshot proof
- Tests don't run clean on Mini
- No TestFlight pipeline
- No real trail testing

## Target State: 10/10

---

## Phase 1: Factory Floor Works (1/10 → 4/10)
**Goal:** One issue ships through the full pipeline without intervention.

### P1.1: Fix Mini Build Environment
- [ ] Ferrostar version synced (DONE — commit 9198f8d6)
- [ ] MapStyleManager duplicate removed (DONE — commit 9c40c200)
- [ ] All XCUITests compile and run on Mini
- [ ] NavHUDGoldStarTests: 8/8 pass on Mini
- [ ] Test file auto-added to Xcode project (not manual pbxproj edits)

### P1.2: Test Runner Completes Full Cycle
- [ ] Pull branch on Mini (git fetch + reset --hard)
- [ ] Build succeeds
- [ ] Run tests (specific suite, not full)
- [ ] Take screenshot
- [ ] Email screenshot to Steve
- [ ] Post results to Forge issue
- [ ] Mark in_review
- [ ] All in one run, no retries

### P1.3: Critique Agent Grades
- [ ] Auto-queued after Test Runner marks in_review
- [ ] Reads Test Runner's screenshot
- [ ] Grades against Gold Star spec
- [ ] Posts element-by-element review
- [ ] If <10/10: rejects with specific fix list, iOS Builder auto-wakes
- [ ] If 10/10: approves, Ship Engineer auto-wakes

### P1.4: Ship Engineer Creates PR
- [ ] Reads QA/Critique approval
- [ ] Rebases on master
- [ ] Creates PR with structured body
- [ ] Emails Steve the PR link

**Exit criteria

*[truncated — see source for full prompt]*