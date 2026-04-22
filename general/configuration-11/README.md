# Configuration

> Default worktree location: `~/.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration

Default worktree location: `~/.local/share/worktrees/<organization>-<repo_name>`.

<div class="lw-callout">
  <p><strong>Find settings quickly:</strong> use the map below, then jump to the relevant settings group.</p>
</div>

## Configuration Map

| If you need to... | Go to |
| --- | --- |
| Change theme, icons, or layout behaviour | [Settings -> Themes / Worktree list and refresh](#settings) |
| Tune filter/search and command palette behaviour | [Settings -> Search and palette](#settings) |
| Adjust diff, pager, and editor integration | [Settings -> Diff, pager, and editor](#settings) |
| Configure automation and notes persistence | [Settings -> Worktree lifecycle](#settings) |
| Configure naming scripts and templates | [Settings -> Branch naming](#settings) |
| Override settings per repository | [Git Configuration](#git-configuration) |

## Global Configuration (YAML)

Reads `~/.config/lazyworktree/config.yaml`. Example (also in [`config.example.yaml`](https://github.com/chmouel/lazyworktree/blob/main/config.example.yaml)):

```yaml
worktree_dir: ~/.local/share/worktrees
sort_mode: switched  # Options: "path", "active" (commit date), "switched" (last accessed)
layout: default      # Pane arrangement: "default" or "top"
auto_refresh: true
refresh_interval: 10  # Seconds
disable_pr: false     # Disable all PR/MR fetching and display (default: false)
icon_set: nerd-font-v3
search_auto_select: false
fuzzy_finder_input: false
palette_mru: true         # Enable MRU (Most Recently Used) sorting for command palette
palette_mru_limit: 5      # Number of recent commands to show (default: 5)
max_untracked_diffs: 10
max_diff_chars: 200000
max_name_length: 95       # Maximum length for worktree names in table display (0 disables truncation)
theme: ""       # Leave empty to auto-detect based on terminal background colour
                # (defaults to "rose-pine" for dark, "dracula-light" for light).
                # Options: see the Themes section below.
git

*[truncated — see source for full prompt]*