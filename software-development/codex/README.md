# Codex

> How to load your Context Stack into the Codex CLI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAI Codex CLI

How to load your Context Stack into the Codex CLI.

Codex reads context from markdown files in a pattern similar to Claude Code: a project-level file in the repo root and a global file for user-wide preferences.


## Context Loading Mechanisms

Codex looks for context in two locations:

1. **Project context** (`AGENTS.md` in the project root): Loaded when Codex runs in that directory
2. **Global instructions** (`~/.codex/instructions.md`): Loaded in every session, regardless of project

Both are plain markdown. No special syntax required.


## Recommended Setup

### Global Instructions: Self and Style

Put your Self and Style layers in the global file. These define who you are and how you work, regardless of project.

**File:** `~/.codex/instructions.md`

```markdown
# About Me

## Professional Identity
[Paste your professional-identity.md content here]

## Communication DNA
[Paste your communication-dna.md content here]

## Values and Boundaries
[Paste your values-and-boundaries.md content here]

## Decision Architecture
[Paste your decision-architecture.md content here]
```

### Project AGENTS.md: Substance and Situation

Put your Substance and Situation layers in the project-level file. These vary by project.

**File:** `<project-root>/AGENTS.md`

```markdown
# Project Context

## Strategic Context
[Paste your strategic-context.md content, filtered to this project]

## Domain Map
[Paste relevant sections from your domain-map.md]

## Tool Ecosystem
[Paste your tool-ecosystem.md content]

## Operating Rhythm
[Paste relevant sections from your operating-rhythm.md]
```

### File Structure

```
~/.codex/
└── instructions.md          # Global: identity, style, values

<project-root>/
└── AGENTS.md                # Project: domain, tools, priorities
```


## What Goes Where

| Component | Location | Reasoning |
|:----------|:---------|:----------|
| professional-identity | Global instructions | Applies everywhere |
| communication-dna | Global instru

*[truncated — see source for full prompt]*