# AGENTS

> Shared configurations and build tools (ESLint, Prettier, TypeScript, Brain Monitor)

**Generated:** 2025-10-13
**Source:** .cursor/rules/*.mdc (auto-g

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tooling Packages - Development Rules for AI Agents

Shared configurations and build tools (ESLint, Prettier, TypeScript, Brain Monitor)

**Generated:** 2025-10-13
**Source:** .cursor/rules/*.mdc (auto-generated from modular rules)
**Context:** monorepo, global, tooling, node, backend

---

## Core Rules (Always Apply)

### 00-meta-rules-system


# Meta-Rules: Rules System Architecture

**⚠️ CRITICAL: READ THIS FIRST BEFORE FOLLOWING ANY OTHER RULES**

This file defines how the rules system works and how to modify it. All AI platforms (Claude, Gemini, Cline, Windsurf, LangGraph agents) must understand this architecture.

## Rules System Architecture

### Source of Truth: Modular .mdc Files
All rules are defined in **modular `.rules.mdc` files** in `.cursor/rules/`:
- `00-meta-rules-system.rules.mdc` - This file (meta-rules)
- `01-foundation.rules.mdc` - Core monorepo foundation
- `02-validation-testing.rules.mdc` - Brain monitor & TDD
- `03-frontend-patterns.rules.mdc` - Component patterns
- `04-react-standards.rules.mdc` - React best practices
- `05-backend-express.rules.mdc` - Express architecture
- `06-backend-functional.rules.mdc` - Functional patterns
- `07-documentation.rules.mdc` - Documentation & versioning
- `08-workflow.rules.mdc` - PR creation & commands
- `09-ai-documentation-maintenance.rules.mdc` - AI documentation maintenance

### Generated Files (DO NOT EDIT)
These files are **auto-generated** from the source `.rules.mdc` files:

**Never edit these files directly:**
- `docs/ai-platforms/CLAUDE.md` (Monorepo root context)
- `apps/web/CLAUDE.md` (React/Frontend context)
- `apps/server/CLAUDE.md` (Express/Backend context)
- `packages/universal/CLAUDE.md` (Universal package context)
- `tooling/CLAUDE.md` (Tooling packages context)
- `docs/ai-platforms/GEMINI.md` (and all other GEMINI.md files)
- `docs/ai-platforms/AGENTS.md` (and all other AGENTS.md files)
- `docs/ai-platforms/.clinerules` (Cline platform)
- `docs/ai-platforms/.windsurfrules` (Windsurf 

*[truncated — see source for full prompt]*