# Claude Code Instructions

> Instructions for Claude Code working in the kg-automation repository.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude Code Instructions — kg-automation

Instructions for Claude Code working in the kg-automation repository.

## Start Every Session By Reading

1. `CLAUDE.md` at repo root — read this first, always
2. `docs/design/felix-capability-roadmap.md` — design intent, capability status, and roadmap
3. `git log --oneline -10` — understand current state before touching anything
4. `git status` — confirm clean working tree

## Role in This System

Claude Code is the **execution layer**. It implements what has been designed.
Architecture decisions live in `docs/design/`. If something isn't in the spec,
stop and ask rather than infer.

## Platform Reality

- **Mac (MacBook Pro)**: authoring and interaction only
- **office2 (Ubuntu 24.04 LTS)**: always-on hub — this is where things run
- **Tailscale**: the network between them
- **Windows**: not supported, does not exist in this system
- **Dropbox**: not used for coordination

When writing scripts or configs, target Linux (office2) unless explicitly told
otherwise.

## Key Services on office2

| Service | Details |
|---|---|
| OpenClaw | Orchestration engine, skills, WhatsApp webhook |
| Vikunja | Docker container, port 3456, SQLite backend |
| Obsidian Sync | `ob sync --continuous` via systemd (`obsidian-sync.service`) |
| Restic | Backups at 4AM to `/mnt/backups/restic-repo` |

Access office2 via Tailscale SSH. Never expose management ports to public internet.

## Skill Files

Existing skills to be migrated from second-brain to office2/OpenClaw:

| Skill | Current location | Status |
|---|---|---|
| inbox-processor | `~/second-brain/.claude/skills/inbox-processor/SKILL.md` | Migrate (FEAT-007) |
| kent-voice | `~/second-brain/.claude/skills/kent-voice/SKILL.md` | Migrate (FEAT-008) |
| vault-writer | `~/second-brain/.claude/skills/vault-writer/SKILL.md` | Migrate (FEAT-009) |

When migrating: add Vikunja API task bridge to inbox-processor, no other
changes to skill logic.

## Git Workflow

- Push directly to main for routi

*[truncated — see source for full prompt]*