# PRODUCT ROADMAP

> **Updated**: 2026-04-06
**Vision**: *CodeFRAME is the project delivery system that turns ideas into verified, deployed code — AI agents write the code

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME Product Roadmap

**Updated**: 2026-04-06
**Vision**: *CodeFRAME is the project delivery system that turns ideas into verified, deployed code — AI agents write the code, CodeFRAME owns everything before and after.*

This is the **single source of truth** for CodeFRAME's product roadmap. All prior planning documents (V2_STRATEGIC_ROADMAP, FEATURE_ROADMAP, IMPLEMENTATION_ROADMAP, etc.) are archived in `docs/archive/`.

This document focuses on gaps in the web product that block the end-to-end vision. It is not a comprehensive feature list. Items included here were selected because they are load-bearing for the Think → Build → Prove → Ship pipeline or because their absence creates a significant hole in the user experience.

### Completed foundation (prior phases)
- **Phases 1–2.5**: CLI foundation, FastAPI server layer, ReAct agent — all complete
- **Phase 3**: Web UI core screens — PRD editor, task board, execution monitor, blocker resolution, diff reviewer, PROOF9 requirements table, interactive agent sessions (`/sessions`) — all complete
- **Phase 4.A–4.D**: Agent adapter protocol (ClaudeCode/Codex/OpenCode/Kilocode), execution environment (worktree isolation, E2B cloud), multi-provider LLM (OpenAI-compatible adapter) — all complete

---

## Current State (verified 2026-04-06)

The golden path works end-to-end in the browser for a single developer on a single project. All core screens exist. What is missing is not *breadth* — it is *depth* in the places the vision depends on most.

---

## Phase 3.5 — Close the Interaction Gap ✅ PARTIAL (A+B complete, C pending)

**The issue**: The web UI is read-heavy. Users watch agents run, view requirements, inspect diffs. But they cannot run quality gates from the browser or capture a glitch and watch it become a permanent proof obligation.

### Milestone A: Bidirectional Agent Chat ✅ COMPLETE (#500–509)

Fully shipped: `/sessions` page, `/sessions/[id]` detail with `SplitPane`, `AgentChatPanel`, `AgentTerminal`, `us

*[truncated — see source for full prompt]*