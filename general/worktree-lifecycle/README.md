# Worktree Lifecycle

> Create a `.wt` file in your repository to run commands when creating or removing worktrees.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Custom Initialisation and Termination

Create a `.wt` file in your repository to run commands when creating or removing worktrees. Format inspired by [wt](https://github.com/taecontrol/wt).

<div class="mint-callout">
  <p><strong>Use this page when:</strong> you want to automate setup or cleanup tasks when worktrees are created or deleted.</p>
</div>

## `.wt` File Format

Place a `.wt` file in your repository root. It uses YAML with two keys: `init_commands` (run after worktree creation) and `terminate_commands` (run before worktree removal).

### Example

```yaml
init_commands:
    - link_topsymlinks
    - cp $MAIN_WORKTREE_PATH/.env $WORKTREE_PATH/.env
    - npm install
    - direnv allow $WORKTREE_PATH
    - docker compose -f $WORKTREE_PATH/docker-compose.yml up -d

terminate_commands:
    - docker compose -f $WORKTREE_PATH/docker-compose.yml down
    - echo "Cleaned up $WORKTREE_NAME"
```

## Environment Variables

The following variables are available to all init and terminate commands:

| Variable | Description | Example |
| --- | --- | --- |
| `WORKTREE_BRANCH` | Branch checked out in the new worktree | `feature/auth` |
| `MAIN_WORKTREE_PATH` | Absolute path to the main (bare) worktree | `/home/user/project` |
| `WORKTREE_PATH` | Absolute path to the new worktree | `/home/user/project-worktrees/feature-auth` |
| `WORKTREE_NAME` | Short name of the worktree | `feature-auth` |

## Execution Order

Commands execute in the order listed. If you also have global `init_commands` or `terminate_commands` in your LazyWorktree configuration file, those run **before** the repository `.wt` commands. This allows global setup (e.g., shell environment) to complete before project-specific commands.

If any command fails (non-zero exit code), subsequent commands in the list still execute — failure does not halt the sequence.

## Special Commands

### `link_topsymlinks`

A built-in command (not a shell command) that automates common worktree setup tasks:

1. **Symlinks untr

*[truncated — see source for full prompt]*