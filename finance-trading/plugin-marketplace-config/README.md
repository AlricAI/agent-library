# PLUGIN MARKETPLACE CONFIG

> ## Purpose

Configure amplihack plugin to be discoverable in Claude Code's plugin marketplace via `extraKnownMarketplaces` setting.

## Problem

Issue

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Plugin Marketplace Configuration

## Purpose

Configure amplihack plugin to be discoverable in Claude Code's plugin marketplace via `extraKnownMarketplaces` setting.

## Problem

Issue #1948 requirement #5 mandates marketplace source: `github.com/rysweet/amplihack`. Currently:

- No marketplace configuration exists
- Plugin won't appear in Claude Code `/plugin` command
- Users cannot discover amplihack via marketplace

## Solution Overview

Add `extraKnownMarketplaces` configuration to settings generation:

1. Add marketplace config to `.claude-plugin/plugin.json`
2. Update `SettingsGenerator` to include marketplace in generated settings
3. Ensure marketplace appears in `~/.claude/settings.json`

## Contract

### Inputs

**Plugin Manifest (`.claude-plugin/plugin.json`):**

```json
{
  "name": "amplihack",
  "marketplace": {
    "name": "amplihack",
    "url": "https://github.com/rysweet/amplihack",
    "type": "github"
  }
}
```

**Settings Generator:**

- Reads manifest marketplace config
- Merges into user settings

### Outputs

**Generated `~/.claude/settings.json`:**

```json
{
  "extraKnownMarketplaces": [
    {
      "name": "amplihack",
      "url": "https://github.com/rysweet/amplihack"
    }
  ],
  "enabledPlugins": ["amplihack"]
}
```

### Side Effects

- Updates `~/.claude/settings.json` with marketplace config
- Makes plugin discoverable via `/plugin` command in Claude Code

## Implementation Design

### File Modifications

```
.claude-plugin/
└── plugin.json               # Modified: Add marketplace section

src/amplihack/settings_generator/
└── generator.py              # Modified: Include marketplace in settings
```

### Change 1: Plugin Manifest (`plugin.json`)

**Location:** `.claude-plugin/plugin.json`

**Current State (lines 1-17):**

```json
{
  "name": "amplihack",
  "version": "0.9.0",
  "description": "AI-powered development framework...",
  "author": {...},
  "homepage": "https://github.com/rysweet/amplihack",
  "repos

*[truncated — see source for full prompt]*