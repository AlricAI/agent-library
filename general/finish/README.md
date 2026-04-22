# Finish

> Create a pull request with comprehensive description following repo best practices

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping create a pull request with a comprehensive description. Your task is to gather information, generate the PR description, push the branch, and create the PR using project conventions.

## Step 1: Load Configuration

Check for configuration and context:

```bash
# Check for config and context files
[ -f ".claude/config.yaml" ] && echo "CONFIG=true" || echo "CONFIG=false"
[ -f ".claude/.pr-context.json" ] && echo "CONTEXT=true" || echo "CONTEXT=false"

# Get current branch
git branch --show-current
```

**Load from `.claude/config.yaml` (if exists):**

```yaml
workflow:
  developmentBranch: staging
  productionBranch: main
pullRequests:
  targetBranch: staging
  reviewers: []
  labels: []
issueTracker:
  type: auto
```

**Load from `.claude/.pr-context.json` (if exists):**

```json
{
  "ticket_id": "PROJ-1234",
  "ticket_url": "https://...",
  "ticket_title": "Ticket title",
  "branch": "fix/proj-1234-description",
  "type": "fix",
  "description": "Short description"
}
```

**Default Values (when no config):**

```yaml
pullRequests:
  targetBranch: staging
  reviewers: []
  labels: []
```

If context file is missing or incomplete:

- Inform the user they should run `/start` and `/commit` first
- Ask for missing information (ticket ID, branch name)

## Step 2: Verify State

Check current git state:

```bash
# Current branch
CURRENT_BRANCH=$(git branch --show-current)

# Commits on this branch vs target
TARGET_BRANCH=$(config.pullRequests.targetBranch || "staging")
git log --oneline ${TARGET_BRANCH}..HEAD

# Any uncommitted changes?
git status --short
```

**Warnings:**

- If uncommitted changes exist: "You have uncommitted changes. Run `/commit` first?"
- If no commits on branch: "No commits to create PR. Make changes and run `/commit` first."
- If on target branch: "You're on the target branch. Switch to a feature branch first."

## Step 3: Gather Changed Files

Analyze what changed:

```bash
# Files changed vs target branch
TARGET_BRANCH=$(config.pull

*[truncated — see source for full prompt]*