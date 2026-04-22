# CLAUDE

> Shared configurations and build tools (ESLint, Prettier, TypeScript, Brain Monitor)

**Generated:** 2025-10-13
**Source:** .cursor/rules/*.mdc (auto-g

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tooling Packages - Development Rules

Shared configurations and build tools (ESLint, Prettier, TypeScript, Brain Monitor)

**Generated:** 2025-10-13
**Source:** .cursor/rules/*.mdc (auto-generated from modular rules)
**Context:** monorepo, global, tooling, node, backend

---

## Table of Contents

1. [00 Meta Rules System](#00-meta-rules-system)
2. [01 Foundation](#01-foundation)
3. [02 Validation Testing](#02-validation-testing)
4. [05 Backend Express](#05-backend-express)
5. [06 Backend Functional](#06-backend-functional)
6. [07 Documentation](#07-documentation)
7. [08 Workflow](#08-workflow)
8. [09 Ai Documentation Maintenance](#09-ai-documentation-maintenance)

---

## 00 Meta Rules System

> **When to apply:** Rules system architecture and modification protocol - ALWAYS read this first

> **Scopes:** monorepo, global


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
- `d

*[truncated — see source for full prompt]*