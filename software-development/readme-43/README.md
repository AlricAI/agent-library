# README

> An automated agent that addresses PR review feedback for skill files, continuing development until the PR is approved.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill PR Addresser

An automated agent that addresses PR review feedback for skill files, continuing development until the PR is approved.

## Quick Start

### Prerequisites

- Python 3.11+
- Claude CLI installed and authenticated
- `gh` CLI authenticated
- `uv` package manager

### Install Dependencies

```bash
cd .claude/agents/skill-pr-addresser
uv sync
```

### Address PR Feedback

```bash
# Address feedback on PR #795
just -f .claude/agents/skill-pr-addresser/justfile address 795

# Dry run (see what would be done)
just -f .claude/agents/skill-pr-addresser/justfile address-dry 795

# Check current status
just -f .claude/agents/skill-pr-addresser/justfile status 795
```

## Commands

| Command | Description |
|---------|-------------|
| `just address <pr>` | Address feedback on a PR |
| `just address-dry <pr>` | Dry run - show what would be done |
| `just address-skill <pr> <skill>` | Address with explicit skill path |
| `just status <pr>` | Check PR addressing status |
| `just sessions` | List active sessions |
| `just sessions-all` | List all sessions (including completed) |
| `just batch [--label X]` | Address all PRs with pending feedback |

## How It Works

### 1. Discovery

Finds PRs with pending feedback:
- Reviews requesting changes
- Unresolved review threads
- Unresolved comments

### 2. Analysis

The `feedback-analyzer` sub-agent (Haiku 3.5) extracts structured feedback items:

```json
{
  "feedback_items": [
    {
      "id": "thread-123",
      "type": "change_request",
      "file": "SKILL.md",
      "line": 42,
      "description": "Add example for Result<T, E>",
      "priority": "high"
    }
  ]
}
```

### 3. Fixing

The `feedback-fixer` sub-agent implements changes with model escalation:
- **Simple nitpicks**: Haiku 3.5 (fast, cheap)
- **Complex changes**: Sonnet 4 (thorough)

### 4. Commit & Push

Changes are committed with a conventional commit message:

```
fix(skills): address PR #795 feedback (iteration 1)

### Changed
- Addressed 3 feed

*[truncated — see source for full prompt]*