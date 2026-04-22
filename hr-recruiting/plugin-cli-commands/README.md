# PLUGIN CLI COMMANDS

> ## Purpose

Provide user-facing CLI commands for installing, uninstalling, and verifying amplihack plugins through the `amplihack plugin` command inte

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Plugin CLI Commands

## Purpose

Provide user-facing CLI commands for installing, uninstalling, and verifying amplihack plugins through the `amplihack plugin` command interface.

## Problem

Issue #1948 requires CLI commands for plugin management, but currently only `PluginManager` backend exists without proper CLI integration. Users cannot easily install, uninstall, or verify plugins via command line.

## Solution Overview

Create three CLI command handlers that wrap the existing `PluginManager` class:

- `plugin install` - Install plugin from source
- `plugin uninstall` - Remove plugin cleanly
- `plugin verify` - Verify installation and discoverability

## Contract

### Inputs

**Command: `amplihack plugin install [source] [options]`**

- `source` (str): Git URL or local path to plugin
- `--force` (bool, optional): Overwrite existing plugin

**Command: `amplihack plugin uninstall [plugin_name]`**

- `plugin_name` (str): Name of plugin to remove

**Command: `amplihack plugin verify [plugin_name]`**

- `plugin_name` (str): Name of plugin to verify
- Returns: Exit code 0 (success) or 1 (failure)

### Outputs

**Install:**

- Success: Prints installation confirmation, location, exit code 0
- Failure: Prints error message, exit code 1

**Uninstall:**

- Success: Prints removal confirmation, exit code 0
- Failure: Prints error message, exit code 1

**Verify:**

- Success: Prints verification report (installed, discoverable, hooks loaded), exit code 0
- Failure: Prints diagnostics, exit code 1

### Side Effects

**Install:**

- Creates plugin directory at `~/.amplihack/.claude/plugins/{plugin_name}/`
- Updates `~/.claude/settings.json` with plugin registration
- Adds plugin to `enabledPlugins` array

**Uninstall:**

- Removes plugin directory
- Removes plugin from `~/.claude/settings.json`
- Removes from `enabledPlugins` array

**Verify:**

- No side effects (read-only operation)

## Implementation Design

### File Structure

```
src/amplihack/
├─

*[truncated — see source for full prompt]*