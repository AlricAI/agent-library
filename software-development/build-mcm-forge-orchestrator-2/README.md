# BUILD MCM FORGE ORCHESTRATOR

> Paste this entire prompt into a new Claude Code session to start building.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# BUILD PROMPT: MCM Forge Orchestrator

Paste this entire prompt into a new Claude Code session to start building.

---

## Mission

Build the MCM Forge Orchestrator — a Paperclip clone that manages AI coding agents. It has three components:

1. **Supabase schema** — 14 tables for agents, issues, runs, routines, costs
2. **Mac Mini orchestrator** — Node.js process that polls Supabase, spawns `claude`/`gemini`/`codex` CLIs
3. **Next.js dashboard on Vercel** — pixel-perfect copy of Paperclip's UI at mcmforge.com

## Your Resources

### Project Plan (1,654 lines — read this FIRST)
`/Users/stevemcmillian/llama-3-agents/Apps/projects/MCMForge/docs/mcm-forge-orchestrator-plan.md`

This contains:
- Full Supabase SQL schema (14 tables, indexes, RLS, ready to apply)
- Mac Mini orchestrator architecture (4 concurrent loops, adapter interface, process management)
- Dashboard page routes and components
- Agent definition format
- 5 build phases with deliverables
- Migration path from Paperclip

### Paperclip UI Screenshots (23 pages — your gold standard)
`/Users/stevemcmillian/llama-3-agents/Apps/projects/MCMForge/qa-screenshots/paperclip-reference/`

Every page of the Paperclip dashboard captured pixel-perfect:
- `paperclip-dashboard.png` — home with agent cards, stats bar
- `paperclip-issues.png` — issue board with filters, priority colors
- `paperclip-issue-detail.png` — issue detail with comments, properties
- `paperclip-agents.png` — agent list with hierarchy, status indicators
- `paperclip-agent-detail.png` — agent dashboard with charts
- `paperclip-agent-instructions.png` — AGENTS.md file editor
- `paperclip-agent-configuration.png` — adapter config form
- `paperclip-agent-runs.png` — run history with tokens, prompts
- `paperclip-agent-skills.png` — skills list
- `paperclip-agent-budget.png` — spend tracking
- `paperclip-org.png` — org chart (React Flow tree)
- `paperclip-skills.png` — skills registry
- `paperclip-routines.png` — routine list with schedules
- `paperclip-

*[truncated — see source for full prompt]*