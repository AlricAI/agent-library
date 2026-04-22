# Git Worktrees

> > One worktree per agent session.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Git Worktrees for Concurrent AI Agent Work

> One worktree per agent session. Zero merge conflicts. Full isolation.

## The Problem

Multiple AI agent sessions working on the same repository cause chaos. Session A is on branch `feature/auth`. Session B switches to `main` to check something. Session A's next tool call fails because the branch disappeared. Or worse: Session B force-pushes over Session A's work.

Traditional solutions don't work:
- Separate clones: waste disk space, slow sync
- Branch locking: blocks parallelism
- Careful coordination: requires manual intervention

The insight: Git worktrees provide isolated working directories sharing the same `.git` repository. Each AI session gets its own worktree. They can't interfere with each other.

## The Pattern

### Worktree Basics

A worktree is a separate working directory linked to the same Git repository.

**Create a worktree:**
```bash
git worktree add ~/worktrees/feature-auth feature/auth
```

This creates:
- Working directory at `~/worktrees/feature-auth`
- Checked out to branch `feature/auth`
- Shares `.git` with main repository
- Independent of other worktrees

**List worktrees:**
```bash
git worktree list
```

**Remove a worktree:**
```bash
git worktree remove ~/worktrees/feature-auth
```

### One Worktree Per AI Session

**Pattern: Isolated Feature Development**

Session A wants to work on authentication:
```bash
cd ~/code/myapp
git worktree add ~/.claude/worktrees/auth feature/auth
cd ~/.claude/worktrees/auth
# AI agent works here, isolated from other sessions
```

Session B wants to work on payments:
```bash
cd ~/code/myapp
git worktree add ~/.claude/worktrees/payments feature/payments
cd ~/.claude/worktrees/payments
# AI agent works here, completely independent
```

**Benefits:**
- Sessions can't switch each other's branches
- No conflicts from simultaneous edits
- No force-push overwrites
- Clean separation of concerns

### Worktree Lifecycle

**1. Create worktree for new feature:**
```bash
#

*[truncated — see source for full prompt]*