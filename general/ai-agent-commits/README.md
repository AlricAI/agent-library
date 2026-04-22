# AI AGENT COMMITS

> This document describes the AI-friendly commit conventions and workflows configured for the ModPorter-AI project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Agent Commits

This document describes the AI-friendly commit conventions and workflows configured for the ModPorter-AI project.

## Overview

The project uses **conventional commits** to enable:
- Automated changelog generation
- Clear commit history for AI analysis
- Consistent message formatting
- Automated commit validation
- AI agent identification

## Setup

### Automatic Setup

Run the setup script once:

```bash
pnpm run setup-ai-commits
```

This will:
1. Install commitlint dependencies
2. Configure husky git hooks
3. Set up the git message template
4. Enable AI agent signing configuration

### Manual Installation

```bash
# Install dependencies
pnpm add -D @commitlint/cli @commitlint/config-conventional husky

# Initialize husky
npx husky install

# Configure git message template
git config commit.template .gitmessage

# Enable AI agent signing
git config user.ai-agent true
```

## Commit Format

All commits must follow the **conventional commits** specification:

```
<type>: <subject> (#issue-number)

<body>

<footer>
```

### Type

Required. Must be one of:

| Type | Description |
|------|-------------|
| `feat` | A new feature |
| `fix` | A bug fix |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `style` | Changes that don't affect code meaning (formatting, whitespace) |
| `perf` | Code change that improves performance |
| `test` | Adding or updating tests |
| `docs` | Documentation changes |
| `chore` | Build process, dependency, or tooling changes |
| `ci` | CI/CD configuration or script changes |
| `revert` | Reverts a previous commit |

### Subject

- Use imperative mood ("add feature", not "added feature")
- Capitalize the first letter
- Do not end with a period
- Limit to 50 characters
- Include issue number in parentheses if applicable

### Body

- Explain **what** and **why**, not how
- Wrap lines at 72 characters
- Separate from subject with a blank line
- Optional but recommended for non-trivial commits

### Fo

*[truncated — see source for full prompt]*