# Guide

> This guide provides detailed examples, patterns, and best practices for using pi-teams.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# pi-teams Usage Guide

This guide provides detailed examples, patterns, and best practices for using pi-teams.

## Table of Contents

- [Getting Started](#getting-started)
- [Common Workflows](#common-workflows)
- [Hook System](#hook-system)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

---

## Getting Started

### Basic Team Setup

First, make sure you're inside a tmux session, Zellij session, or iTerm2:

```bash
tmux  # or zellij, or just use iTerm2
```

Then start pi:

```bash
pi
```

Create your first team:

> **You:** "Create a team named 'my-team'"

Set a default model for all teammates:

> **You:** "Create a team named 'Research' and use 'gpt-4o' for everyone"

---

## Common Workflows

### 1. Code Review Team

> **You:** "Create a team named 'code-review' using 'gpt-4o'"
> **You:** "Spawn a teammate named 'security-reviewer' to check for vulnerabilities"
> **You:** "Spawn a teammate named 'performance-reviewer' using 'haiku' to check for optimization opportunities"
> **You:** "Create a task for security-reviewer: 'Review the auth module for SQL injection risks' and set it to in_progress"
> **You:** "Create a task for performance-reviewer: 'Analyze the database queries for N+1 issues' and set it to in_progress"

### 2. Refactor with Plan Approval

> **You:** "Create a team named 'refactor-squad'"
> **You:** "Spawn a teammate named 'refactor-bot' and require plan approval before they make any changes"
> **You:** "Create a task for refactor-bot: 'Refactor the user service to use dependency injection' and set it to in_progress"

Teammate submits a plan. Review it:

> **You:** "List all tasks and show me refactor-bot's plan for task 1"

Approve or reject:

> **You:** "Approve refactor-bot's plan for task 1"

> **You:** "Reject refactor-bot's plan for task 1 with feedback: 'Add unit tests for the new injection pattern'"

### 3. Testing with Automated Hooks

Create a hook script at `.pi/team-hooks/task_completed.sh`:

```bash
#!/bin/ba

*[truncated — see source for full prompt]*