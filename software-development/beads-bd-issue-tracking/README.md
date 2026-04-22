# Beads (bd) Issue Tracking

> Beads (bd) Issue Tracking **Note:** This skill must execute on demand only. This project uses **bd** (beads) for issue tracking. Run `bd onboard` to get started.

## System Prompt
# Beads (bd) Issue Tracking

**Note:** This skill must execute on demand only.

This project uses **bd** (beads) for issue tracking. Run `bd onboard` to get started.

## Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work atomically
bd close <id>         # Complete work
bd sync               # Sync with git
```
<!-- BEGIN BEADS INTEGRATION -->
## Issue Tracking with bd (beads)

**IMPORTANT**: This project uses **bd (beads)** for ALL issue tracking. Do NOT use markdown TODOs, task lists, or other tracking methods.

### Why bd?

- Dependency-aware: Track blockers and relationships between issues
- Git-friendly: Auto-syncs to JSONL for version control
- Agent-optimized: JSON output, ready work detection, discovered-from links
- Prevents duplicate tracking systems and confusion

### Quick Start

**Check for ready work:**

```bash
bd ready --json
```

**Create new issues:**

```bash
bd create "Issue title" --description="Detailed context" -t bug|feature|task -p 0-4 --json
bd create "Issue title" --description="What this issue is about" -p 1 --deps discovered-from:bd-123 --json
```

**Fill issue fields correctly:**

- Put the short problem/request summary in `--description`
- Put implementation approach, constraints, and technical notes in `--design`
- Put verification checklist / done criteria in `--acceptance`
- Always set the correct type explicitly with `-t bug|feature|task|epic|chore`
- For long or multi-line content, prefer `--body-file` / `--design-file` instead of large inline shell strings
- After creating or updating an issue, verify the stored fields with `bd show <id> --json`

**Recommended pattern for substantial issues:**

```bash
bd create "Issue title" \
  --description "Short summary of the problem or requested feature" \
  --design "Implementation notes, constraints, and architecture decisions" \
  --acceptance "- First acceptance check\n- Second acceptance c

*[truncated — see source for full prompt]*