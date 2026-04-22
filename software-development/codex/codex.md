---
name: Codex
description: How to load your Context Stack into the Codex CLI.
model: claude-sonnet-4-5
---
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
| communication-dna | Global instructions | Applies everywhere |
| values-and-boundaries | Global instructions | Applies everywhere |
| decision-architecture | Global instructions | Applies everywhere |
| operating-rhythm | Global instructions | Applies everywhere |
| domain-map | Project AGENTS.md | Varies by project focus |
| tool-ecosystem | Project AGENTS.md | Varies by project stack |
| strategic-context | Project AGENTS.md | Varies by project |
| feedback-journal | Global instructions | Corrections apply broadly |
| brand-voice | Project AGENTS.md | Only if project involves content |
| collaboration-profile | Omit | Rarely relevant in CLI context |
| learning-edge | Project AGENTS.md | Relevant for new-domain projects |


## Writing Effective AGENTS.md

Codex uses AGENTS.md primarily for task execution, so structure it around what Codex needs to do good work in your project:

```markdown
# Project Context

## What This Project Is
A backend API for healthcare provider scheduling. Built with Node.js,
TypeScript, and PostgreSQL. Follows domain-driven design with clear
bounded contexts.

## My Expertise
I am senior in API design, TypeScript, and healthcare IT systems. Assume
I understand architectural tradeoffs. Skip introductory explanations for
these domains. I am still learning GraphQL federation; provide more
detail there.

## Coding Standards
- TypeScript strict mode. No `any` types.
- Error handling: explicit try/catch with typed errors. No silent failures.
- Functions under 30 lines. Files under 400 lines.
- Tests for every public function. Minimum 80% coverage.
- Immutable data patterns. Return new objects, never mutate inputs.

## Current Focus
Building the provider availability service. Priority is correctness
over performance. Timezone handling is the hardest part.
```

Notice how this blends context-component content with project-specific technical details. The AGENTS.md file is where your Context Stack meets the concrete realities of the project.


## Token Considerations

Codex has context limits. Keep your files focused:

- **Global instructions**: Under 1,500 words. This loads every session.
- **AGENTS.md**: Under 2,000 words. Focus on what Codex needs for the current project.

If your content exceeds these targets, prioritize the information that most directly affects code quality and task execution.


## AGENTS.md and Version Control

Unlike global instructions, AGENTS.md lives in the project root and can be committed to version control. This is useful if:

- Your team shares coding standards
- You want consistent AI behavior across contributors
- You want the file to evolve alongside the codebase

If you commit it, keep personal context (identity, style preferences) in your global instructions file and put only shared project context in AGENTS.md.


## Testing Your Setup

Start a Codex session and give it a task that exercises your context:

```
Write a function to validate provider availability slots, handling
timezone edge cases.
```

Evaluate whether:
- The code follows your stated coding standards
- Error handling matches your preferences
- The complexity level matches your stated expertise
- Variable naming and structure match your style

If the output feels generic, strengthen the coding standards and domain expertise sections in your AGENTS.md.