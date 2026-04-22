# Substack Article

> ## The Problem Nobody Talks About

AI coding assistants have gotten remarkably good at writing code. Claude can implement features, fix bugs, and even

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# I Automated My Entire Git Workflow with AI - Here's How

## The Problem Nobody Talks About

AI coding assistants have gotten remarkably good at writing code. Claude can implement features, fix bugs, and even write tests.

But here's what I noticed: the code is only half the job.

Every feature still requires:
- Creating a branch with the right naming convention
- Fetching context from the ticket
- Writing meaningful commit messages
- Creating PRs with proper descriptions
- Managing releases with changelogs
- Keeping branches in sync

These tasks eat hours every week. They're repetitive, error-prone, and frankly... boring.

So I built a solution.

## Introducing Claude Code Commands

Over the past few months, I've developed a set of 10 slash commands that automate the entire development workflow. Today I'm open-sourcing them.

**The Core Workflow:**
```
/start TICKET-123    → Create feature branch, fetch ticket context
[write your code]
/commit              → Stage changes, conventional commit message
/finish              → Push and create PR with full description
```

That's it. From ticket to pull request in minutes, not hours.

## The Commands

### `/start` - Begin with Context

Instead of manually creating branches and looking up ticket details, `/start TICKET-123` does it all:

- Creates a branch following your naming conventions
- Fetches the ticket title, description, and acceptance criteria
- Saves context for later use in commits and PRs

Works with Linear, Jira, and GitHub Issues.

### `/tdd` - AI-Enforced Test-Driven Development

This is my favorite command. `/tdd` implements the RED-GREEN-REFACTOR cycle automatically:

1. **RED**: Writes failing tests based on acceptance criteria
2. **GREEN**: Implements code until all tests pass
3. **REFACTOR**: Cleans up without breaking tests

No more "I'll add tests later." The AI enforces discipline.

### `/commit` - Conventional Commits, Every Time

Tired of inconsistent commit messages? `/commit` analyzes your ch

*[truncated — see source for full prompt]*