---
name: Beads (bd) Issue Tracking
description: Beads (bd) Issue Tracking **Note:** This skill must execute on demand only. This project uses **bd** (beads) for issue tracking. Run `bd onboard` to get started.
---
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
  --acceptance "- First acceptance check\n- Second acceptance check" \
  -t feature -p 2 --json
```

**Recommended pattern for long specs:**

```bash
bd create "Issue title" \
  --body-file issue-description.txt \
  --design-file issue-design.txt \
  --acceptance "- Acceptance check 1\n- Acceptance check 2" \
  -t feature -p 2 --json
bd show <id> --json
```

**Claim and update:**

```bash
bd update <id> --claim --json
bd update bd-42 --priority 1 --json
```

**Complete work:**

```bash
bd close bd-42 --reason "Completed" --json
```

### Issue Types

- `bug` - Something broken
- `feature` - New functionality
- `task` - Work item (tests, docs, refactoring)
- `epic` - Large feature with subtasks
- `chore` - Maintenance (dependencies, tooling)

### Priorities

- `0` - Critical (security, data loss, broken builds)
- `1` - High (major features, important bugs)
- `2` - Medium (default, nice-to-have)
- `3` - Low (polish, optimization)
- `4` - Backlog (future ideas)

### Workflow for AI Agents

1. **Check ready work**: `bd ready` shows unblocked issues
2. **Claim your task atomically**: `bd update <id> --claim`
3. **Work on it**: Implement, test, document
4. **Discover new work?** Create linked issue:
   - `bd create "Found bug" --description="Short summary" --design="Technical details and constraints" --acceptance="- Repro is covered\n- Fix is verified" -p 1 --deps discovered-from:<parent-id>`
5. **Complete**: `bd close <id> --reason "Done"`
6. **Push**: Automatically commit and push changes for this task immediately (see Landing the Plane below).

### Auto-Sync

bd automatically syncs with git:

- Exports to `.beads/issues.jsonl` after changes (5s debounce)
- Imports from JSONL when newer (e.g., after `git pull`)
- No manual export/import needed!

### Beads UI

You can launch a local web interface to visualize and manage issues:

```bash
bdui start --open
```

This starts a server at http://127.0.0.1:3000.

### Important Rules

- ✅ Use bd for ALL task tracking
- ✅ Always use `--json` flag for programmatic use
- ✅ Link discovered work with `discovered-from` dependencies
- ✅ Check `bd ready` before asking "what should I work on?"
- ❌ Do NOT create markdown TODO lists
- ❌ Do NOT use external issue trackers
- ❌ Do NOT duplicate tracking systems

For more details, see README.md and docs/QUICKSTART.md.

<!-- END BEADS INTEGRATION -->