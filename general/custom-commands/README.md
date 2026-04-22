# Custom Commands

> Custom commands let you bind shell commands, tmux sessions, zellij sessions, OCI container execution, or output views to keys.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Custom Commands

Custom commands let you bind shell commands, tmux sessions, zellij sessions, OCI container execution, or output views to keys. Commands can appear in help/footer and in the command palette. Prefix a command key with `_` to make it command-palette only.

<div class="lw-callout">
  <p><strong>Defaults:</strong> <code>t</code> opens tmux and <code>Z</code> opens zellij. Override either key with your own command definition.</p>
</div>

## Quick Start Patterns

=== "Simple command"

    ```yaml
    custom_commands:
      universal:
        e:
          command: nvim
          description: Editor
          show_help: true
    ```

=== "Show command output"

    ```yaml
    custom_commands:
      universal:
        o:
          command: git status -sb
          description: Status
          show_output: true
    ```

=== "Tmux session"

    ```yaml
    custom_commands:
      universal:
        t:
          description: Tmux
          tmux:
            session_name: "wt:$WORKTREE_NAME"
            attach: true
            on_exists: switch
            windows:
              - name: shell
                command: zsh
              - name: lazygit
                command: lazygit
    ```

=== "Container command"

    ```yaml
    custom_commands:
      universal:
        C:
          command: "go test ./..."
          description: Tests in container
          show_output: true
          container:
            image: "golang:1.22"
    ```

=== "Container + tmux"

    ```yaml
    custom_commands:
      universal:
        ctrl+l:
          description: Dev container
          tmux:
            session_name: "dev:$WORKTREE_NAME"
            windows:
              - name: test
                command: "go test -v ./..."
              - name: shell
          container:
            image: "golang:1.22"
            extra_args:
              - "--network=host"
    ```

=== "Container (image only)"

    ```yaml
    custom_commands:
      universal:
        ctrl+d:
   

*[truncated — see source for full prompt]*