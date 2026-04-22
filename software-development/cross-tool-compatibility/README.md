# CROSS TOOL COMPATIBILITY

> ## Purpose

Ensure amplihack plugin works with Claude Code, GitHub Copilot, AND Codex by verifying compatibility and documenting differences.

## Prob

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Cross-Tool Compatibility Strategy

## Purpose

Ensure amplihack plugin works with Claude Code, GitHub Copilot, AND Codex by verifying compatibility and documenting differences.

## Problem

Issue #1948 requirement #6: "Compatibility: Claude Code, GitHub Copilot, AND Codex". Currently:

- Plugin designed for Claude Code
- Unknown compatibility with GitHub Copilot plugin format
- Unknown compatibility with Codex plugin format
- No compatibility testing or documentation

## Solution Overview

Three-phase approach:

1. **Research Phase:** Document plugin formats for each tool
2. **Compatibility Matrix:** Identify differences and required adaptations
3. **Testing Phase:** Verify plugin works or document limitations

## Contract

### Inputs

**Plugin Manifest (`.claude-plugin/plugin.json`):**

- Current format (Claude Code)
- May need variants for other tools

**Hook Configuration (`hooks.json`):**

- Current format uses Claude Code lifecycle hooks
- May need adaptation for other tools

### Outputs

**Compatibility Report:**

- Document what works out-of-box
- Document required adaptations
- Document known limitations
- Provide migration guidance

**Adapted Configurations (if needed):**

- `.copilot-plugin/plugin.json` (if format differs)
- `.codex-plugin/plugin.json` (if format differs)
- Tool-specific hook configurations

### Side Effects

- May create tool-specific plugin configurations
- Documents compatibility matrix in README

## Implementation Design

### Phase 1: Research (No Code)

**Research Questions:**

1. **GitHub Copilot:**
   - Does Copilot support plugin architecture?
   - What is the plugin manifest format?
   - Does it support hooks? What lifecycle events?
   - Does it support `${PLUGIN_ROOT}` variable substitution?

2. **Codex:**
   - Does Codex support plugin architecture?
   - What is the plugin manifest format?
   - Does it support hooks? What lifecycle events?
   - Does it support path variable substitution?

**Research Sourc

*[truncated — see source for full prompt]*