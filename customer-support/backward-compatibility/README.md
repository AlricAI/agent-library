# BACKWARD COMPATIBILITY

> ## Purpose

Ensure existing per-project `~/.amplihack/.claude/` installations continue working while supporting the new plugin architecture.

## Probl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Backward Compatibility Pattern

## Purpose

Ensure existing per-project `~/.amplihack/.claude/` installations continue working while supporting the new plugin architecture.

## Problem

Issue #1948 moves to plugin architecture (`~/.amplihack/.claude/`), but:

- Existing projects use per-project `~/.amplihack/.claude/` directories
- Users may prefer local over global plugin installation
- Migration path unclear
- Risk of breaking existing workflows

## Solution Overview

Implement dual-mode support:

1. **Detection:** Automatically detect per-project vs plugin installation
2. **Preference:** Local `~/.amplihack/.claude/` takes precedence over plugin
3. **Fallback:** Plugin used if no local installation
4. **Migration:** Provide tools to migrate between modes

## Contract

### Inputs

**Detection Function:**

```python
def detect_claude_mode() -> ClaudeMode:
    """Detect whether to use project-local or plugin mode."""
```

**Environment:**

- Current working directory (may have `~/.amplihack/.claude/`)
- Plugin directory (`~/.amplihack/.claude/`)
- User preference (explicit override)

### Outputs

**ClaudeMode:**

```python
class ClaudeMode(Enum):
    LOCAL = "local"      # Project has .claude/ directory
    PLUGIN = "plugin"    # Use plugin from ~/.amplihack/.claude/
    NONE = "none"        # No .claude found
```

**Behavior:**

- `LOCAL`: Use project's `~/.amplihack/.claude/` directory
- `PLUGIN`: Use plugin installation
- `NONE`: Install plugin or create local (user choice)

### Side Effects

- May create `~/.amplihack/.claude/.mode` file to record user preference
- Logs mode selection for debugging
- No automatic migration (user-initiated only)

## Implementation Design

### File Structure

```
src/amplihack/
├── cli.py                    # Modified: Add mode detection
└── mode_detector/
    ├── __init__.py           # NEW: Exports detect_claude_mode
    ├── detector.py           # NEW: Detection logic
    └── migrator.py           # NEW:

*[truncated — see source for full prompt]*