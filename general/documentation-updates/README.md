# DOCUMENTATION UPDATES

> ## Purpose

Update all documentation to reflect plugin architecture migration and provide clear installation instructions for users.

## Problem

Issu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Documentation Updates

## Purpose

Update all documentation to reflect plugin architecture migration and provide clear installation instructions for users.

## Problem

Issue #1948 requires documentation updates but currently:

- README still describes per-project `~/.amplihack/.claude/` installation
- No plugin installation instructions
- No migration guide
- CLI help text outdated
- PROJECT.md doesn't describe plugin architecture

## Solution Overview

Update six documentation files with plugin architecture information:

1. **README.md** - Installation section
2. **.claude/context/PROJECT.md** - Architecture description
3. **CLI help text** - Plugin commands
4. **MIGRATION_GUIDE.md** - Per-project → Plugin migration
5. **PLUGIN_ARCHITECTURE.md** - Technical details (new)
6. **CHANGELOG.md** - Version 0.9.0 changes

## Contract

### Inputs

**Current Documentation State:**

- README.md: Per-project installation instructions
- PROJECT.md: Generic template
- No plugin-specific documentation

**New Content Needed:**

- Plugin installation steps
- Migration guidance
- Architecture explanation
- CLI command reference

### Outputs

**Updated Documentation:**

- Clear plugin installation instructions
- Migration path from per-project mode
- Architecture diagrams/explanation
- Updated CLI help text

### Side Effects

- Users see updated installation instructions
- Reduces support questions about installation
- Provides migration clarity

## Implementation Design

### File 1: README.md Updates

**Section:** Installation

**Current (Per-Project):**

````markdown
## Installation

```bash
pip install amplihack
amplihack install
```
````

This copies `~/.amplihack/.claude/` directory to your project.

````

**New (Plugin Mode):**
```markdown
## Installation

### Quick Start (Recommended - Plugin Mode)

```bash
# Install amplihack
pip install amplihack

# Install plugin (one-time setup)
amplihack plugin install https://github.com/rysweet/amplihack

# Laun

*[truncated — see source for full prompt]*