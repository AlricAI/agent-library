# Cloud Automation

> ## Goal

Enable the AGI Agent Kit to integrate with Claude's cloud-native features: **Cowork** (desktop VM agent), **Cloud Tasks** (24/7 scheduled run

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cloud Automation Directive

## Goal

Enable the AGI Agent Kit to integrate with Claude's cloud-native features: **Cowork** (desktop VM agent), **Cloud Tasks** (24/7 scheduled runs), **Channels** (Telegram/Discord remote control), and **Scheduled Tasks** (local cron). This provides full automation without human interaction after one-time setup.

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                   Automation Tiers                       │
├──────────────┬──────────────┬──────────────┬────────────┤
│ Local Agent  │ Cowork       │ Cloud Tasks  │ Channels   │
│ (CLI/IDE)    │ (Desktop VM) │ (24/7 cloud) │ (Telegram) │
├──────────────┼──────────────┼──────────────┼────────────┤
│ You control  │ Runs skills  │ Runs on      │ Remote     │
│ the terminal │ in isolated  │ Anthropic    │ trigger    │
│              │ VM, reads    │ servers,     │ via phone  │
│              │ local files  │ never fails  │ to desktop │
├──────────────┼──────────────┼──────────────┼────────────┤
│ Worktrees +  │ Dispatch via │ Setup via    │ /plugin    │
│ Qdrant       │ mobile app   │ claude.ai    │ install    │
│ memory       │ or schedule  │ /code web UI │ telegram   │
└──────────────┴──────────────┴──────────────┴────────────┘
         ↕ All tiers share Qdrant memory ↕
```

## Tier 1: Local Agent Automation

What the framework already provides. Run in terminal, fully autonomous.

```bash
# Autonomous loop (runs every 10 minutes, expires after 3 days)
/loop 10m Check for new PRs on main branch and review them

# Scheduled local task (daily/weekly via Claude desktop app)
# Created via: Claude Desktop → Scheduled tab → New Task
```

**Integration:** Use `execution/worktree_isolator.py` for parallel agent isolation. Use `execution/dispatch_agent_team.py --parallel` for team dispatch.

## Tier 2: Cowork (Desktop VM Agent)

Cowork runs skills in an isolated VM on your desktop. It can read/write local files, connect to Gmail/Slack/Calendar via MCP c

*[truncated — see source for full prompt]*