# Claude Code

> How to load your Context Stack into Claude Code (the CLI agent).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude Code

How to load your Context Stack into Claude Code (the CLI agent).

Claude Code is the deepest integration point for your Context Stack. It reads markdown files automatically at session start, with no manual copy-paste required. Your context is always present, always active.


## How Context Loading Works

Claude Code reads context from three locations, in this order:

1. **Global context** (`~/.claude/CLAUDE.md`): Loaded in every session, regardless of project
2. **Project context** (`CLAUDE.md` in your project root): Loaded when you run Claude Code from that directory
3. **Memory files** (`~/.claude/projects/<project-path>/memory/MEMORY.md`): Persistent per-project memory with an index that points to individual memory files

All three are plain markdown. No special syntax required.


## Recommended Setup

### Global CLAUDE.md: Your Self Layer

Put Self and Style components in your global file. These apply to every project and rarely change.

**File:** `~/.claude/CLAUDE.md`

```markdown
# About Me

## Professional Identity
<!-- Paste your professional-identity.md content here -->

## Communication DNA
<!-- Paste your communication-dna.md content here -->

## Values and Boundaries
<!-- Paste your values-and-boundaries.md content here -->

## Operating Rhythm
<!-- Paste your operating-rhythm.md content here -->

## Decision Architecture
<!-- Paste your decision-architecture.md content here -->
```

**What this gives you:** Every Claude Code session starts with your Self and Style layers loaded: your professional identity, communication patterns, values, and decision frameworks.

### Project CLAUDE.md: Your Substance and Situation Layers

Put Substance and Situation components in each project's context file. These vary by project.

**File:** `<project-root>/CLAUDE.md`

```markdown
# Project Context

## Strategic Context
<!-- Paste your strategic-context.md content here, filtered to this project -->

## Domain Map
<!-- Paste relevant sections from your dom

*[truncated — see source for full prompt]*