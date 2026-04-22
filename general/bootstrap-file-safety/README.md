# BOOTSTRAP FILE SAFETY

> ## Problem Fixed

The `scripts/bootstrap_enhanced.sh` script was **silently overwriting existing user files** without warning or backup, causing poten

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bootstrap File Safety Fix

## Problem Fixed

The `scripts/bootstrap_enhanced.sh` script was **silently overwriting existing user files** without warning or backup, causing potential data loss. This violated basic UX principles and could destroy user customizations.

## Solution Implemented

### 1. Safe File Creation Function

Added `create_file_safely()` function that:
- **Checks for existing files** before creating new ones
- **Preserves existing content** by default
- **Only overwrites with explicit `--force` flag**
- **Handles edge cases**: symlinks, directories, permission errors
- **Provides clear user feedback** about what's happening

### 2. Enhanced User Communication

**Help Text Updates:**
```bash
File Safety:
  By default, existing files are preserved (not overwritten).
  Use --force to overwrite existing files. Backups are automatically created.
  Check for warnings about skipped files during normal runs.
```

**Improved Warning Messages:**
- Clear indication when files are skipped
- Guidance on how to override (`--force`)
- Information about automatic backups
- Specific handling for symlinks and directories

### 3. Edge Case Handling

**Directory Conflicts:**
```bash
error "Cannot create file: path is a directory"
```

**Symlink Handling:**
```bash
warn "Skipping existing symlink: path"
warn "  → Use --force to overwrite (will replace symlink with regular file)"
```

**Permission Errors:**
```bash
error "Cannot write file: path (permission denied?)"
```

## Files Affected

The following files are now created safely:
- `dev.md` - Development log
- `.agents/agents.md` - Agent instructions
- `.claude/commands/plan.md` - Claude command templates
- `docs/CLAUDE.md` - Claude Code overlay
- `docs/GEMINI.md` - Gemini CLI overlay
- `docs/qwen.md` - Qwen Code overlay

## Usage Examples

### Normal Run (Preserves Existing Files)
```bash
./scripts/bootstrap_enhanced.sh
# Output: [WARN] Skipping existing file: docs/CLAUDE.md
#         [WARN]   → Use --force to ove

*[truncated — see source for full prompt]*