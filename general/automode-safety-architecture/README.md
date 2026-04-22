# Automode Safety Architecture

> ## Problem Statement

When amplihack is launched via `uvx --from git+...` in a directory with uncommitted git changes, the UVX initialization copies `

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture Specification: Auto Mode Safety (Issue #1090)

## Problem Statement

When amplihack is launched via `uvx --from git+...` in a directory with uncommitted git changes, the UVX initialization copies `~/.amplihack/.claude/` directory contents and silently overwrites local uncommitted changes, causing irreversible data loss.

## Solution Overview

Implement a safety layer that:

1. Detects conflicts between files to be copied and uncommitted git changes
2. Uses fallback temporary directory when conflicts exist
3. Transforms auto mode prompts to include directory change instruction
4. Maintains transparency (no behavior change except protection)

## Architecture Design

### Philosophy Alignment

- **Ruthless Simplicity**: Three focused modules with single responsibilities
- **Zero-BS Implementation**: No stubs, complete implementations only
- **Modular Design (Bricks)**: Each module is self-contained with clear contracts
- **Regeneratable**: Can be rebuilt from this specification alone

### Module Structure

```
src/amplihack/safety/
├── __init__.py                    # Module exports
├── git_conflict_detector.py       # Brick 1: Detect conflicts
├── safe_copy_strategy.py          # Brick 2: Determine copy target
└── prompt_transformer.py          # Brick 3: Transform prompts
```

---

## Module 1: Git Conflict Detector

### Purpose

Detect if files we're about to copy conflict with uncommitted git changes.

### Contract

**Inputs:**

- `target_dir: str | Path` - Directory where we want to copy
- `essential_dirs: list[str]` - List of subdirectories to check (e.g., ["agents/amplihack", "commands/amplihack"])

**Outputs:**

- `ConflictDetectionResult` dataclass:
  - `has_conflicts: bool` - True if conflicts exist
  - `conflicting_files: list[str]` - List of conflicting file paths
  - `is_git_repo: bool` - True if target_dir is in a git repo

**Side Effects:**
None (read-only)

### Implementation Specification

```python
from dataclasses import dataclass
from 

*[truncated — see source for full prompt]*