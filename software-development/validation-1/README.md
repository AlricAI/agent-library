# VALIDATION

> This document describes the validation and catalog management workflow for Claude Code elements (agents, skills, commands).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Element Validation & Catalog Management

This document describes the validation and catalog management workflow for Claude Code elements (agents, skills, commands).

## Quick Start

### Complete Validation Workflow

Run the complete workflow to validate, fix, and update the catalog:

```bash
make validate-and-sync
```

This runs three steps automatically:
1. **Validate** all elements (project + global)
2. **Auto-fix** validation errors
3. **Regenerate** catalog manifests

## Individual Commands

### 1. Validate YAML Frontmatter

Check all elements for valid YAML frontmatter without making changes:

```bash
make validate
```

**What it checks:**
- Required fields (name, description)
- Field types (string vs list)
- Name patterns (lowercase, hyphens only)
- Max lengths
- YAML syntax

**Output:**
- ✅ Valid files (quiet mode only shows errors)
- ❌ Invalid files with error details
- Summary statistics

### 2. Auto-Fix Validation Errors

Automatically fix common validation issues:

```bash
make validate-fix
```

**What it fixes:**
- Missing frontmatter delimiters (`---`)
- List-to-string conversions (`allowed-tools`)
- Invalid name patterns
- Missing required fields (adds placeholders)

**Important:** Review changes before committing!

### 3. Update Catalog Manifests

Regenerate catalog manifests from validated elements:

```bash
make catalog-sync
```

**What it does:**
- Scans `.claude/` directories (project + global)
- Validates all elements (skips invalid)
- Generates JSON manifests in `manifests/`
- Shows catalog statistics

**Output files:**
- `manifests/agents.json`
- `manifests/skills.json`
- `manifests/commands.json`

## Sync to Global

Copy project `.claude/` files to global `~/.claude/`:

```bash
make sync-global          # One-time copy
make watch-sync           # Auto-sync on changes (development)
```

Use `sync-push` for intelligent syncing with conflict resolution:

```bash
make sync-push            # Interactive sync project → global
make sync-pull       

*[truncated — see source for full prompt]*