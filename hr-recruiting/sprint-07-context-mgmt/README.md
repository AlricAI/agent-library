# Sprint 07 Context Mgmt

> **Status**: 🚧 In Progress - Phases 2-5 Complete
**Duration**: Week 7 (In Progress)
**Epic/Issues**: cf-31 through cf-35, cf-36 (cf-36 exists in beads

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sprint 7: Context Management

**Status**: 🚧 In Progress - Phases 2-5 Complete
**Duration**: Week 7 (In Progress)
**Epic/Issues**: cf-31 through cf-35, cf-36 (cf-36 exists in beads, open)
**Test Status**: ✅ 59/59 tests passing (100%)

## Goal
Implement Virtual Project system to prevent context pollution and enable long-running agent sessions.

## User Story
As a developer, I want to see agents intelligently manage their memory, keeping relevant context hot and archiving old information.

## Planned Tasks

### Core Features (P0)
- [ ] **cf-NEW-31**: ContextItem storage (Status: Schema exists, no implementation)
  - Save context items to DB (context_items table ready)
  - Track importance scores
  - Access count tracking
  - Demo: Context items stored and queryable

- [ ] **cf-NEW-32**: Importance scoring algorithm (Status: Not started)
  - Calculate scores based on type, age, access
  - Automatic tier assignment (HOT/WARM/COLD)
  - Score decay over time
  - Demo: Items auto-tier based on importance

- [ ] **cf-NEW-33**: Context diffing and hot-swap (Status: Not started)
  - Calculate context changes
  - Load only new/updated items
  - Remove stale items
  - Demo: Agent context updates efficiently

- [ ] **cf-NEW-34**: Flash save before compactification (Status: Stub with TODO)
  - Detect context >80% of limit
  - Create checkpoint
  - Archive COLD items
  - Resume with fresh context
  - NOTE: WorkerAgent.flash_save() exists but has TODO (worker_agent.py:48-51)
  - Demo: Agent continues after flash save

### Enhancements (P1)
- [ ] **cf-NEW-35**: Context visualization in dashboard (Status: Not started)
  - Show tier breakdown (HOT/WARM/COLD)
  - Token usage per tier
  - Item list with importance scores
  - Demo: Inspect what agent "remembers"

- [ ] **cf-36**: Claude Code Hooks Integration (Status: Open in beads)
  - Integrate with Claude Code hooks system
  - before_compact hook for flash save
  - State preservation during compactification
  - Estimated Effort: 2-3

*[truncated — see source for full prompt]*