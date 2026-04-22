# Cli

> The CLI supports listing, creating, deleting, renaming, and executing commands in worktrees without launching the full TUI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Usage

The CLI supports listing, creating, deleting, renaming, and executing commands in worktrees without launching the full TUI.

<div class="lw-callout">
  <p><strong>Quick command cookbook:</strong> <code>lazyworktree list</code>, <code>lazyworktree create ...</code>, <code>lazyworktree delete ...</code>, and <code>lazyworktree exec ...</code>.</p>
</div>

## Config Overrides

```bash
lazyworktree --worktree-dir ~/worktrees

# Override config values from CLI
lazyworktree --config lw.theme=nord --config lw.sort_mode=active
```

## Listing Worktrees

```bash
lazyworktree list              # Table output (default)
lazyworktree list --pristine   # Paths only (scripting)
lazyworktree list --json       # JSON output
lazyworktree ls                # Alias
```

`--pristine` and `--json` are mutually exclusive.

## Creating Worktrees

```bash
lazyworktree create                          # Auto-generated from current branch
lazyworktree create my-feature               # Explicit name
lazyworktree create my-feature --with-change # With uncommitted changes
lazyworktree create --from-branch main my-feature
lazyworktree create --from-pr 123
lazyworktree create --from-issue 42          # From issue (base: current branch)
lazyworktree create --from-issue 42 --from-branch main  # From issue with explicit base
lazyworktree create -I                       # Interactively select issue (fzf or list)
lazyworktree create -I --from-branch main    # Interactive issue with explicit base
lazyworktree create -P                       # Interactively select PR (fzf or list)
lazyworktree create -P -q "dark"             # Pre-filter interactive PR selection
lazyworktree create -I --query "login"       # Pre-filter interactive issue selection
lazyworktree create --from-pr 123 --no-workspace        # Branch only, no worktree
lazyworktree create --from-issue 42 --no-workspace      # Branch only, no worktree
lazyworktree create -I --no-workspace                    # Interactive issue, branch

*[truncated — see source for full prompt]*