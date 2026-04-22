# Commit

> Stage and commit changes with proper formatting following repo conventions

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping commit changes for a pull request. Your task is to stage changes, generate a properly formatted commit message following project conventions, and handle pre-commit hooks.

## Step 1: Load Configuration

Check for configuration and context:

```bash
# Check for config and context files
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
[ -f ".claude/.pr-context.json" ] && echo "CONTEXT=true" || echo "CONTEXT=false"
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
commits:
  format: "[{type}] {message} ({ticket})"
  types: [Feature, Fix, Hotfix, Refactor, Docs, Test, Chore]
  requireTicket: false
  ticketPattern: "^[A-Z]+-\\d+$"
attribution:
  enabled: false
  format: "Co-Authored-By: Claude <noreply@anthropic.com>"
```

**Load from `.claude/.pr-context.json` (if exists):**

```json
{
  "ticket_id": "PROJ-1234",
  "type": "fix",
  "branch": "fix/proj-1234-description"
}
```

**Default Values (when no config):**

```yaml
commits:
  format: "[{type}] {message} ({ticket})"
  types: [Feature, Fix, Hotfix, Refactor, Docs, Test, Chore]
  requireTicket: false
attribution:
  enabled: false
```

## Step 2: Gather Context

If `.pr-context.json` doesn't exist or is incomplete, ask for missing information:

### Missing Ticket ID

If `commits.requireTicket: true` or no ticket found in context:

**Question**: "What is the ticket ID for this commit?"

- Example: `PROJ-1234`, `ENG-456`
- Allow skipping if `requireTicket: false`

### Missing Change Type

If type not found in context:

**Question**: "What type of change is this?"

**Options**: Feature, Fix, Hotfix, Refactor, Docs, Test, Chore

## Step 3: Show Changed Files

Display what will be staged:

```bash
# Show git status
git status --short

# Show detailed diff stats
git diff --stat
git diff --cached --stat
```

Present to user:

```
Changes to be committed:

Staged:
  M src/file1.ts
  A src/file2.ts

Unstaged:
  M src/file3.ts
  M tests/file1.test.ts

Do you want to stage al

*[truncated — see source for full prompt]*