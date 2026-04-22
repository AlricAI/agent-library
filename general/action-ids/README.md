# Action Ids

> Use these IDs in the `keybindings:` section of your configuration file to bind any key to a built-in palette action.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Action IDs Reference

Use these IDs in the `keybindings:` section of your configuration file to bind any key to a built-in palette action. Keybindings use a pane-scoped structure where `universal` bindings apply everywhere and pane-specific sections override them when that pane is focused.

**Valid pane scope names:** `universal`, `worktrees`, `info`, `status`, `log`, `notes`, `agent_sessions`

```yaml
keybindings:
  universal:
    G: git-lazygit
    ctrl+d: worktree-delete
    F: git-fetch
  worktrees:
    x: worktree-delete
  log:
    d: git-diff
```

Keys defined in `keybindings:` take priority over `custom_commands` and built-in keys. The bound key is also displayed as the shortcut in the command palette. Pane-specific bindings override universal ones for the same key.

---

## Git Operations

| ID | Label | Default Key | Description |
|----|-------|-------------|-------------|
| `git-diff` | Show diff | `d` | Show diff for current worktree or commit |
| `git-refresh` | Refresh | `r` | Reload worktrees |
| `git-fetch` | Fetch remotes | `R` | git fetch --all |
| `git-push` | Push to upstream | `P` | git push (clean worktree only) |
| `git-sync` | Synchronise with upstream | `S` | git pull, then git push (clean worktree only) |
| `git-fetch-pr-data` | Fetch PR data | `p` | Fetch PR/MR status from GitHub/GitLab |
| `git-ci-checks` | View CI checks | `v` | View CI check logs for current worktree |
| `git-pr` | Open in browser | `o` | Open PR, branch, or repo in browser |
| `git-lazygit` | Open LazyGit | `g` | Open LazyGit in selected worktree |
| `git-run-command` | Run command | `!` | Run arbitrary command in worktree |

## Status Pane

| ID | Label | Default Key | Description |
|----|-------|-------------|-------------|
| `status-stage-file` | Stage/unstage file | `s` | Stage or unstage selected file |
| `status-commit-staged` | Open commit screen | `c` | Open the commit screen for staged changes (or prompt to stage all) |
| `status-commit-all` | Commit changes 

*[truncated — see source for full prompt]*