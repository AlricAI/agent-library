# Worktree Support

> Power Steering now works seamlessly across git worktrees, providing consistent workflow validation and counter persistence regardless of where you work in your repository structure.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Power Steering Worktree Support

Power Steering now works seamlessly across git worktrees, providing consistent workflow validation and counter persistence regardless of where you work in your repository structure.

## What Changed

Previously, Power Steering had issues when working in git worktrees:

- `.disabled` file detection failed (only checked current directory)
- Block counters reset on every invocation (no shared state)
- No hard maximum enforcement (potential infinite loops)
- Confusing error messages

These issues are now resolved. Power Steering works identically in worktrees and standard repositories.

## Quick Start

### Using Power Steering in Worktrees

Power Steering automatically detects worktree environments and uses shared state directories. No configuration changes required.

```bash
# Create a worktree
git worktree add ../feature-branch feature-branch

# Work in the worktree
cd ../feature-branch

# Power Steering works normally
# - Block counter persists across invocations
# - .disabled file detection works from any location
# - Hard maximum prevents infinite loops
```

### Disabling Power Steering

Create a `.disabled` file in any of these locations (checked in order):

1. **Current working directory**: `touch .disabled`
2. **Shared Git directory**: `touch $(git rev-parse --git-common-dir)/.claude/runtime/power-steering/.disabled`
3. **Project root**: `cd $(git rev-parse --show-toplevel) && touch .disabled`

Power Steering checks all three locations automatically.

```bash
# Example: Disable from worktree
cd /path/to/worktree
touch .disabled

# Or disable globally for all worktrees
touch "$(git rev-parse --git-common-dir)/.claude/runtime/power-steering/.disabled"
```

## Features

### Worktree Detection

Power Steering automatically detects git worktrees using `git rev-parse --git-common-dir`:

```python
from amplihack.tools.amplihack.git_utils import (
    get_common_git_dir,
    is_worktree
)

# Check if current directory is a worktree
if 

*[truncated — see source for full prompt]*