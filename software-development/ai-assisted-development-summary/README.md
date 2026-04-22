# AI ASSISTED DEVELOPMENT SUMMARY

> This repository is a toolkit for AI-assisted software development.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Dev Toolkit Summary

This repository is a toolkit for AI-assisted software development. It is not an app and it is not a framework you import into production code. Its job is to help AI coding agents work with better context, safer defaults, clearer workflows, and more repeatable results.

## The Fastest Way to Get Value

If you are new to this repository, do this first:

1. Pick the instruction surface your agent already reads.
2. Copy one baseline rules file into your project.
3. Add context, review, and testing patterns only after the rules file is working.

Then map that generic path to the tool you use:

- `rules/CLAUDE.md` for Claude Code and compatible tools
- `rules/AGENTS.md` for Codex CLI
- `rules/COPILOT.md` for GitHub Copilot
- `rules/GEMINI.md` for Gemini CLI and related Gemini surfaces
- `rules/ANTIGRAVITY.md` for Antigravity
- the tool-specific rule files for Cursor and Windsurf

Copy the matching file into your project root. That gives your agent a basic identity, coding standards, workflow rules, testing expectations, security rules, and delivery guardrails before the first prompt.

You do not need the full installer to benefit from this repository.
You also do not need to care about companies, training, plugins, or machine bootstrap on day one.

## What This Repository Contains

### 1. Rules

The `rules/` directory contains drop-in instruction files for different AI tools.

Use these when you want the agent to automatically respect:

- your coding standards
- trunk-based workflow
- testing and verification gates
- documentation rules
- security boundaries
- durable execution expectations

Think of rules as the always-loaded behavior layer.

### 2. Patterns

The `patterns/` directory contains workflow playbooks. These explain how to use AI well, not just what to tell the model.

The pattern set covers:

- context building
- task orchestration
- code review
- testing
- memory systems
- multi-model routing
- session management
- git worktrees
- p

*[truncated — see source for full prompt]*