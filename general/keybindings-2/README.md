# Keybindings

> <div class="lw-callout">
  <p><strong>Tip:</strong> use this page by context. Start with global controls, then jump to the pane you are working in.</p

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Key Bindings

<div class="lw-callout">
  <p><strong>Tip:</strong> use this page by context. Start with global controls, then jump to the pane you are working in.</p>
</div>

## Jump by Context

- [Global Controls](#global-controls)
- [Pane Focus and Layout](#pane-focus-and-layout)
- [Notes and Taskboard](#notes-and-taskboard)
- [Commit Pane](#commit-pane)
- [Commit File Tree](#commit-file-tree)
- [Status Pane](#status-pane)
- [Git Status Pane](#git-status-pane)
- [Filter and Search Modes](#filter-and-search-modes)
- [Command History and Palette](#command-history-and-palette)
- [Mouse Controls](#mouse-controls)

## Global Controls

| Key | Action |
| --- | --- |
| `Enter` | Jump to worktree (exit and `cd`) |
| `j`, `k` | Move selection up/down in lists and menus |
| `c` | Create new worktree (from branch, commit, PR/MR, or issue) |
| `e` | Open the worktree metadata menu (description, colour, notes, icon, tags) |
| `T` | Open Taskboard (grouped markdown checkbox tasks across worktrees) |
| `m` | Rename selected worktree |
| `D` | Delete selected worktree |
| `d` | View diff in pager (worktree or commit, depending on pane) |
| `A` | Absorb worktree into main |
| `X` | Prune merged worktrees and stale branches (refreshes PR data, checks merge status; stale branches require `prune_stale_branches` config) |
| `!` | Run arbitrary command in selected worktree (with command history) |
| `v` | View CI checks (Enter opens browser, `Ctrl+v` opens logs in pager) |
| `o` | Open PR/MR in browser (or root repo in editor if main branch with merged/closed/no PR) |
| `ctrl+p`, `:` | Command palette |
| `g` | Open LazyGit |
| `r` | Refresh list (also refreshes PR/MR/CI for current worktree) |
| `R` | Fetch all remotes |
| `S` | Synchronise with upstream (pull + push, requires clean worktree) |
| `P` | Push to upstream (prompts to set upstream if missing) |
| `f` | Filter focused pane (worktrees, files, commits) |
| `/` | Search focused pane (incremental) |
| `alt+n`, `alt+p` | Move 

*[truncated — see source for full prompt]*