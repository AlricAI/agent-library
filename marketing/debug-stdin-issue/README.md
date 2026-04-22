# Debug Stdin Issue

> ## Status

The Bun stdin contention theory has been **ruled out**. The wrapper handoff is confirmed working — Bun exits completely (code 10) before SS

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Debug: stdin issue after TUI session selection

## Status

The Bun stdin contention theory has been **ruled out**. The wrapper handoff is confirmed working — Bun exits completely (code 10) before SSH starts. Yet the user reports the issue persists on macOS (darwin-arm64, v1.1.34).

## What we know

### Confirmed working
- `~/.local/bin/vpscli` is the bash wrapper script (verified with `file`)
- `~/.vpscli/bin/vpscli-core` is v1.1.34 (verified with `--version`)
- Wrapper has `stty sane` before exec
- Exit-code-10 path fires correctly (no leftover `/tmp/vpscli-exec-*` files)
- Bun process is fully dead before SSH starts

### The handoff flow (working correctly)
```
1. User runs `vpscli`
2. Wrapper sets VPSCLI_EXEC_FILE=/tmp/vpscli-exec-$, runs vpscli-core
3. vpscli-core renders Ink TUI, user picks a session
4. sshInteractive() writes SSH command to $VPSCLI_EXEC_FILE
5. process.exit(10)
6. Wrapper detects exit code 10, reads exec file
7. Wrapper runs: stty sane 2>/dev/null && exec bash -c "$cmd"
8. bash execs: ssh -t '-o' 'StrictHostKeyChecking=accept-new' dev@13.250.2.78 'bash ~/.vpscli/session.sh start ...'
```

### Minor bug (not the cause)
The wrapper has `VPSCLI_EXEC_FILE="/tmp/vpscli-exec-$"` (single `$`) instead of `$$` (PID). This was likely installed by an older binary. The `ensureWrapperInstalled()` auto-bootstrap in index.ts uses the same WRAPPER_SCRIPT from update.ts which has `$$`. This only affects PID uniqueness for concurrent runs — doesn't break the handoff.

## What to investigate

Since Bun is dead before SSH starts, the issue is NOT Bun stdin contention. Possible causes:

### 1. Terminal state not fully reset
Ink leaves the terminal in raw mode. `stty sane` should fix it, but maybe it's not enough.

**Diagnostic:**
```bash
# Add debug output to the wrapper temporarily
# Edit ~/.local/bin/vpscli and add before the exec line:
#   stty -a > /tmp/vpscli-stty-before.log 2>&1
#   stty sane 2>/dev/null
#   stty -a > /tmp/vpscli-stty-after.log 2>&1

# The

*[truncated — see source for full prompt]*