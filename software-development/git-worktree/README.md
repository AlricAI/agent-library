# GIT WORKTREE

> Guidelines for parallel development using git worktrees, enabling multiple AI agents or developers to work on separate features simultaneously.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Git Worktree Guidelines

Guidelines for parallel development using git worktrees, enabling multiple AI agents or developers to work on separate features simultaneously.

**Related:** [CLAUDE.md](../CLAUDE.md)

## Overview

Git worktrees allow you to check out multiple branches simultaneously in separate directories. This is particularly useful for:

- Running multiple AI agents on different features in parallel
- Quick context switching without stashing changes
- Testing changes in one branch while developing in another
- Reviewing PRs while keeping your work-in-progress intact

## Directory Structure

Recommended layout for this project:

```
~/.openclaw/workspace/
├── monsoftsolutions.com/           # Main repository (main branch)
└── monsoftsolutions.com-worktrees/ # Worktrees directory
    ├── feat-new-feature/
    ├── fix-bug-123/
    └── docs-update/
```

**Important:** Keep worktrees adjacent to (not inside) the main repo to avoid git tracking issues.

## Essential Commands Reference

| Command               | Purpose                   |
| --------------------- | ------------------------- |
| `git worktree add`    | Create new worktree       |
| `git worktree list`   | Show all worktrees        |
| `git worktree remove` | Delete worktree           |
| `git worktree prune`  | Clean up stale references |

## Workflow for AI Agents

### Step-by-Step Process

1. **Create worktree**

   ```bash
   git worktree add ../monsoftsolutions.com-worktrees/feat-name -b feat/feature-name
   ```

2. **Navigate to worktree**

   ```bash
   cd ../monsoftsolutions.com-worktrees/feat-name
   ```

3. **Install dependencies**

   ```bash
   npm install
   ```

4. **Start dev server** (use alternate port if needed)

   ```bash
   npm run dev
   # Or with custom port:
   npm run dev -- --port 4322
   ```

5. **Work on feature** — Make changes, test locally

6. **Commit and push** — Regular git workflow

   ```bash
   git add .
   git commit -m "feat: add feature description"
   gi

*[truncated — see source for full prompt]*