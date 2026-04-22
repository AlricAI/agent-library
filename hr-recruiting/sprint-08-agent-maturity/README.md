# Sprint 08 Agent Maturity

> **Status**: ⚠️ Schema Only
**Duration**: Week 8 (Planned)
**Epic/Issues**: cf-36 through cf-39 (Need new IDs)

## Goal
Enable agents to learn and impr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sprint 8: Agent Maturity

**Status**: ⚠️ Schema Only
**Duration**: Week 8 (Planned)
**Epic/Issues**: cf-36 through cf-39 (Need new IDs)

## Goal
Enable agents to learn and improve over time, graduating from detailed instructions to autonomous operation.

## User Story
As a developer, I want to watch agents graduate from needing detailed instructions to working autonomously as they gain experience.

## Planned Tasks

### Core Features (P0)
- [ ] **cf-NEW-36**: Agent metrics tracking (Status: Schema exists, never populated)
  - Track success rate, blockers, tests, rework
  - Store in agents.metrics JSON field (field exists)
  - Update after each task
  - Demo: Metrics visible in dashboard

- [ ] **cf-NEW-37**: Maturity assessment logic (Status: Stub with TODO)
  - Calculate maturity based on metrics
  - Promote/demote based on performance
  - Store maturity level in DB (field exists)
  - NOTE: WorkerAgent.assess_maturity() exists but has TODO (worker_agent.py:45-47)
  - Demo: Agent auto-promotes after good performance

- [ ] **cf-NEW-38**: Adaptive task instructions (Status: Not started)
  - D1 (Directing): Detailed step-by-step
  - D2 (Coaching): Guidance + examples
  - D3 (Supporting): Minimal instructions
  - D4 (Delegating): Goal only
  - Demo: Instructions change based on maturity

### Enhancements (P1)
- [ ] **cf-NEW-39**: Maturity visualization (Status: Not started)
  - Show current maturity level
  - Display metrics chart
  - Show progression history
  - Demo: See agent growth over time

## Definition of Done
- [ ] Metrics tracked for all agents (success rate, blocker frequency, test pass rate, rework rate)
- [ ] Maturity levels auto-adjust based on performance
- [ ] Task instructions adapt to maturity (D1/D2/D3/D4 templates)
- [ ] Dashboard shows maturity and metrics
- [ ] Agents become more autonomous over time (measured over 20+ tasks)
- [ ] Working demo of agent progressing from D1 → D3

## Current Status

**What Exists**:
- Database field: `agents.matur

*[truncated — see source for full prompt]*