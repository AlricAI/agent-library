# MIGRATION GUIDE

> Guide fer migratin' from per-project `~/.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Migration Guide: Per-Project t' Plugin

Guide fer migratin' from per-project `~/.amplihack/.claude/` installations t' the global plugin architecture.

## Overview

This guide helps ye transition from copyin' `~/.amplihack/.claude/` into each project t' usin' the global plugin at `~/.amplihack/.claude/`.

**Command note:** This guide uses `amplihack claude` in examples. `amplihack launch` still works as a compatibility alias, but `claude` be the preferred explicit command in user-facing docs.

**Migration Path:**

```
Before (Per-Project)              After (Plugin)
─────────────────────             ──────────────
~/project1/.claude/    ────┐
~/project2/.claude/    ────┼────▶  ~/.amplihack/.claude/
~/project3/.claude/    ────┘          (single installation)
```

## Benefits o' Plugin Mode

### Automatic Updates

- Plugin updates affect all projects instantly
- No need t' copy `~/.amplihack/.claude/` to each project
- Always use latest agents and commands

### Consistent Behavior

- Same workflow across all projects
- Standardized agent responses
- Predictable hook behavior

### Simplified Management

- One location fer all customizations
- Easier t' track changes
- Simpler backup and version control

### Disk Space Savings

- One `~/.amplihack/.claude/` directory instead o' N copies
- 50MB saved per project (typical)
- Example: 10 projects = 500MB saved

## When t' Migrate

### Recommended Cases

**✅ Migrate t' Plugin When:**

- Ye work on multiple projects
- Ye want automatic updates across all projects
- Ye use standard amplihack without customizations
- Ye want zero-configuration setup

**Example Workflow:**

```bash
# Install plugin once
amplihack plugin install

# All projects use plugin automatically
cd ~/project1 && amplihack claude  # Uses plugin
cd ~/project2 && amplihack claude  # Uses same plugin
cd ~/project3 && amplihack claude  # Still uses plugin
```

### Keep Per-Project Mode

**🏴‍☠️ Stay Per-Project When:**

- Ye need project-specific agent custom

*[truncated — see source for full prompt]*