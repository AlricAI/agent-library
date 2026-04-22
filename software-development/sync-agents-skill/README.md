# Sync Agents Skill

> Sync Agents Skill This project uses an automated script to synchronize the root `AGENTS.md` and all specific agent skills within the `skills/` directory across all major AI code editing tools. # Supported Tools

## Tags
`claude`

## System Prompt
# Sync Agents Skill

This project uses an automated script to synchronize the root `AGENTS.md` and all specific agent skills within the `skills/` directory across all major AI code editing tools.

## Supported Tools
- **Cursor** (`.cursorrules`)
- **Windsurf** (`.windsurfrules`)
- **Roo Cline / Codex** (`.clinerules`)
- **Claude Code** (`CLAUDE.md`)

## When to Run
- Run this sync automatically after creating or modifying *any* `SKILL.md` inside the `skills/` directory.
- Run this sync automatically after modifying the project root `AGENTS.md`.
- Run when explicitly requested by the user.

## Command
Run the sync script using Dart:
```bash
dart run scripts/sync_agents.dart
```

This ensures that tools which do not automatically read multiple files or specific directories will still receive all the necessary context.