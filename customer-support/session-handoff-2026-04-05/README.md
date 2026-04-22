# SESSION HANDOFF 2026 04 05

> ## What Was Built

MCM Forge went from concept to working fleet in one session. Steve's custom Paperclip is live.

### Mac Mini Fleet (24/7)
| Service

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Session Handoff — 2026-04-05

## What Was Built

MCM Forge went from concept to working fleet in one session. Steve's custom Paperclip is live.

### Mac Mini Fleet (24/7)
| Service | Status | Details |
|---------|--------|---------|
| **Claude Code** | tmux `claude` | Max, Opus 4.6, dirtsyncapp@gmail.com |
| **Codex** | tmux `codex` | Pro, GPT-5.3 codex-1 |
| **Gemini** | tmux `gemini` | AI Ultra, Gemini 3 |
| **Forge Orchestrator** | PM2 pid 49279 | 5 loops, agent API on :3200 |

### Agents (all enabled, idle, $50/month budget each)
| Agent | CLI | Model | Role |
|-------|-----|-------|------|
| Forge COO | Claude | Opus | Triage, delegate, enforce quality gates |
| Forge Builder | Codex | GPT-5.3 | Implement features, fix bugs, create PRs |
| Forge QA | Gemini | gemini-2.5-pro | Playwright screenshots, per-criterion PASS/FAIL |
| Forge Reviewer | Gemini | gemini-2.5-pro | 5-point PR review checklist |
| Fleet Auditor | Gemini | gemini-2.5-flash | Daily 8AM health check (CLI versions, config audit, budget, disk) |

### Infrastructure Built
- **Agent API** (localhost:3200) — 7 REST endpoints: /me, /inbox, /issues, /checkout, /context, create, update
- **[SILENT] marker** — agents with empty inbox skip notifications
- **FTS5 session search** — SQLite cross-run memory, agents recall their last 3 results
- **CWD isolation** — COO in company dir (no code access), Builder/QA/Reviewer in repo root
- **Builder→QA auto-handoff** — when Builder marks issue 'in_review', orchestrator auto-creates QA subtask
- **Shared wiki** — ~/.forge/companies/mcm-forge/wiki/ (ARCHITECTURE, DECISIONS, SESSIONS, PATTERNS, BUGS, GLOSSARY)
- **Plugins** — superpowers, playwright, supabase, context7, frontend-design (all installed + enabled)
- **Supabase MCP** — configured with access token

### Pipeline Proven E2E
```
Steve created FORGE-2 "Issues need attach files" on phone
  → Orchestrator detected in 3 seconds
  → COO woke, triaged, created FORGE-3, assigned to Builder ($0.27)
  → Builder 

*[truncated — see source for full prompt]*