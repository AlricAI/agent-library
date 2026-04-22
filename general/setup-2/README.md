# Setup

> Interactive setup for MCP servers and project configuration

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping set up Claude Code commands for this project. Your task is to interactively configure MCP servers for issue tracker integration and optionally set up the workflow configuration.

## Step 1: Welcome and Context

Display a welcome message:

```
Welcome to Claude Code Commands Setup!

This will help you configure:
- Issue tracker integration (Linear, Jira, GitHub Issues)
- MCP server configuration
- Workflow settings (optional)
```

Check for existing configuration:

```bash
# Check for existing settings
if [ -f ".claude/settings.json" ]; then
  echo "PROJECT_SETTINGS=exists"
fi
if [ -f "$HOME/.claude/settings.json" ]; then
  echo "GLOBAL_SETTINGS=exists"
fi
if [ -f ".claude/config.yaml" ]; then
  echo "CONFIG_YAML=exists"
fi
```

## Step 2: Issue Tracker Selection

Ask the user which issue tracker(s) they use (use AskUserQuestion tool with multiSelect: true):

**Question**: "Which issue tracker(s) do you use?"

**Options**:
- `Linear` - Linear.app for issue tracking
- `Jira` - Atlassian Jira
- `GitHub Issues` - GitHub's built-in issue tracking
- `None` - No issue tracker integration needed

**Note**: Users can select multiple options (e.g., Linear + GitHub Issues).

## Step 3: Jira Configuration (Conditional)

If user selected Jira, ask for the instance URL:

**Question**: "What is your Jira instance URL?"

**Header**: "Jira URL"

**Options**:
- Provide a text input example: `https://your-company.atlassian.net`

Validate the URL format:
- Must start with `https://`
- Must end with `.atlassian.net` (for cloud) or be a valid domain

## Step 4: Settings Location

Ask where to save the MCP server configuration:

**Question**: "Where should the MCP server configuration be saved?"

**Options**:
- `Project (.claude/settings.json)` - Recommended for team sharing, committed to repo
- `Global (~/.claude/settings.json)` - Personal setup, applies to all projects

**Default**: Project-level (first option)

## Step 5: Generate Settings

Based on selections, generate

*[truncated — see source for full prompt]*