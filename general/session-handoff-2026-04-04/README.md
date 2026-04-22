# SESSION HANDOFF 2026 04 04

> ## What Was Built Today (11 PRs: #25-#35)

### Phase 1: Orchestrator Core
- 14 Supabase tables in `forge` schema (companies, agents, issues, runs, rou

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCM Forge Session Handoff — 2026-04-04

## What Was Built Today (11 PRs: #25-#35)

### Phase 1: Orchestrator Core
- 14 Supabase tables in `forge` schema (companies, agents, issues, runs, routines, etc.)
- `forge-orchestrator/` — 22 TypeScript source files
- Adapters: Claude, Gemini, Codex CLI
- Loops: run-executor (5s), heartbeat-scheduler (30s), routine-scheduler (60s), orphan-reaper, mention-watcher (30s)
- Services: wakeup, cost-ledger, issue-lifecycle, mention-parser, session-manager, git worktree
- Dry-run mode: `FORGE_DRY_RUN=true` tests pipeline without CLI
- Budget enforcement: auto-pause agents exceeding monthly limit

### Phase 2: Dashboard (Paperclip Mirror)
- 24 Next.js routes, dark theme (#0d1117 bg, #00d4aa accent)
- Dual-nav sidebar: icon rail (company switcher) + main sidebar (nav, projects, agents, company section)
- Company scoping: cookie + React context, defaults to mcm-forge
- All pages filter by active company
- 5 creation forms (issues, agents, routines, goals, projects)
- All CRUD actions wired (Server Actions)
- Realtime hooks for live updates
- Agent API: /api/agent/me, /api/agent/issues, checkout, create, update

### Agent Onboarding
- 4 agents × 4 files (AGENTS.md, HEARTBEAT.md, SOUL.md, TOOLS.md)
- Forge coordination skill (companies/mcm-forge/skills/forge/SKILL.md)
- Multi-CLI strategy: Gemini builds (15 turns), Codex tests (10 turns), Claude reviews (3 turns)

### Data
- Migrated from Paperclip: 39 DirtSync agents, 89 issues, 23 routines
- MCM Forge team: Forge Builder (Gemini), Forge QA (Codex), Forge COO (Claude Opus), Forge Reviewer (Claude Opus)
- 6 goals in hierarchy (vision → strategy → task)
- All agents paused, all routines paused

## Current State

### Deployed
- Dashboard: mcmforge.com (Vercel, auto-deploy from main)
- Orchestrator: pm2 on Mac Mini (dirtsyncmini@100.125.184.57), PID changes on restart
- Auth: steve@linkschoice.com / MCMForge2026!

### Scorecard: 15A, 32B, 2C, 0D, 3F
- See `docs/FORGE-READINESS-SCORECARD.md`

*[truncated — see source for full prompt]*