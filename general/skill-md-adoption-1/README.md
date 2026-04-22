# skill-md-adoption

> Vendor-neutral unit-of-procedural-knowledge spec enabling cross-tool skill discovery and auto-invocation.

## Model
- **Default:** `claude-sonnet-4-5`

## Tags
`skills` `standards` `discoverability`

## System Prompt
> **Tradução pendente.** Consulte a versão em inglês em [patterns/skill-md-adoption.md](https://github.com/lucassantana-dev/ai-dev-toolkit/blob/main/patterns/skill-md-adoption.md).

# SKILL.md Adoption: Vendor-Neutral Skill Discovery

SKILL.md is an open specification released by Anthropic in 2025 that standardizes how tools discover and auto-invoke procedural knowledge (skills, patterns, guides, rules). Instead of each tool (Claude, Cursor, VSCode, CLI) maintaining isolated skill registries, SKILL.md enables a single skill to be published once and auto-invoked across any tool that speaks the spec.

> _Analog: npm packages aren't Node-specific—they work in browsers, Deno, and serverless runtimes. SKILL.md does for procedural knowledge what package specs do for code: decouple the artifact from the runtime._

## Why SKILL.md matters

**Before**: Skills were vendor silos. A "deployment checklist" skill lived in Claude's `.claude/skills/`, and Cursor had its own copy in `.cursor/skills/`. Updates didn't sync. Different formats. No discovery API.

**After**: One SKILL.md published to a shared registry. Claude, Cursor, VSCode, and CLI tools discover it via `forge-kit install`, call it with the same trigger phrase, and get identical behavior.

## The SKILL.md format

A SKILL is a Markdown file with frontmatter + structured sections. Minimal viable example:

```markdown
---
name: validate-commit-msg
description: Check commit messages against team conventions.
triggers:
  - "validate commit"
  - "check message"
  - "commit lint"
version: "1.0.0"
---

# Validate Commit Message

Ensures commits follow the [Conventional Commits](https://conventionalcommits.org) standard.

## Purpose

Catch malformed commit messages before they land in the repo. Saves code review friction and maintains a searchable git log.

## Invocation

- **Claude**: `validate commit`
- **Cursor**: Trigger inline, or use Command Palette
- **CLI**: `forge-kit invoke validate-commit-msg <message>`

## Example



*[truncated — see source for full prompt]*