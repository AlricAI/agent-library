# Tdd

> Implement a ticket using Test-Driven Development (RED-GREEN-REFACTOR)

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping implement a ticket using Test-Driven Development (TDD). Your task is to guide the user through the RED-GREEN-REFACTOR cycle: write failing tests first, implement code to pass tests, then refactor while keeping tests green.

## Step 1: Load Configuration

Check for configuration and context:

```bash
# Check for config and context files
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
[ -f ".claude/.pr-context.json" ] && echo "CONTEXT=true" || echo "CONTEXT=false"
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
qa:
  tdd:
    confirmBeforeGreen: true
    confirmBeforeRefactor: true
    maxRedAttempts: 3
    runFullSuiteEachPhase: false
    autoStartServer: false
testing:
  unit: auto
  lint: auto
  typeCheck: auto
issueTracker:
  type: auto
```

**Default Values (when no config):**

```yaml
qa:
  tdd:
    confirmBeforeGreen: true
    confirmBeforeRefactor: true
    maxRedAttempts: 3
    runFullSuiteEachPhase: false
    autoStartServer: false
```

## Step 2: Parse Arguments

Extract from `$ARGUMENTS`:

```text
$ARGUMENTS
```

**Patterns to Extract:**

| Pattern     | Example                              | Meaning              |
| ----------- | ------------------------------------ | -------------------- |
| Ticket ID   | `PROJ-123`, `ENG-456`                | Issue tracker ticket |
| GitHub Issue | `#789`                              | GitHub issue number  |
| Linear URL  | `https://linear.app/.../ENG-456/...` | Extract ticket ID    |
| Jira URL    | `https://....atlassian.net/browse/PROJ-123` | Extract ticket ID |

**Parsing Logic:**

- Extract ticket ID from URL if provided
- Linear: Pattern `/issue/([A-Z]+-\d+)/`
- Jira: Pattern `/browse/([A-Z]+-\d+)`
- GitHub: Pattern `issues/(\d+)` or `#(\d+)`

**Validation:**

- Ticket ID is required for TDD workflow
- If not provided, prompt the user for it

## Step 3: Fetch Ticket Details

### Auto-Detect Issue Tracker Type

Based on ticket format and available MCP servers

*[truncated — see source for full prompt]*