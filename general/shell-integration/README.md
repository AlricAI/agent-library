# Shell Integration

> Shell helpers change directory to the selected worktree on exit.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Shell Integration

Shell helpers change directory to the selected worktree on exit. Optional but recommended.

## Quick Usage

Without helper functions, use the simple command form in any POSIX-like shell:

```bash
cd "$(lazyworktree)"
```

With helper functions loaded, you can wrap this in a reusable shell command and preserve consistent behaviour across repositories.

## Shell Setup

=== "Bash"

    **Option A:** Source the helper from a local clone:

    ```bash
    # Add to .bashrc
    source /path/to/lazyworktree/shell/functions.bash

    jt() { worktree_jump $(git rev-parse --show-toplevel) "$@"; }
    ```

    **Option B:** Download the helper:

    ```bash
    mkdir -p ~/.shell/functions
    curl -sL https://raw.githubusercontent.com/chmouel/lazyworktree/refs/heads/main/shell/functions.bash -o ~/.shell/functions/lazyworktree.bash

    # Add to .bashrc
    source ~/.shell/functions/lazyworktree.bash

    jt() { worktree_jump $(git rev-parse --show-toplevel) "$@"; }
    ```

    **With completion:**

    ```bash
    source /path/to/lazyworktree/shell/functions.bash

    jt() { worktree_jump $(git rev-parse --show-toplevel) "$@"; }
    _jt() { _worktree_jump $(git rev-parse --show-toplevel); }
    complete -o nospace -F _jt jt
    ```

    **Jump to last-selected worktree:**

    ```bash
    alias pl='worktree_go_last $(git rev-parse --show-toplevel)'
    ```

=== "Zsh"

    **Option A:** Source the helper from a local clone:

    ```zsh
    # Add to .zshrc
    source /path/to/lazyworktree/shell/functions.zsh

    jt() { worktree_jump $(git rev-parse --show-toplevel) "$@"; }
    ```

    **Option B:** Download the helper:

    ```zsh
    mkdir -p ~/.shell/functions
    curl -sL https://raw.githubusercontent.com/chmouel/lazyworktree/refs/heads/main/shell/functions.zsh -o ~/.shell/functions/lazyworktree.zsh

    # Add to .zshrc
    source ~/.shell/functions/lazyworktree.zsh

    jt() { worktree_jump $(git rev-parse --show-toplevel) "$@"; }
    ```

    **With c

*[truncated — see source for full prompt]*