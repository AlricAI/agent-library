# WALKTHROUGH

> > A hands-on tour of the floop learning loop — from first correction to automatic behavior.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Walkthrough: Teach Your Agent in 5 Minutes

> A hands-on tour of the floop learning loop — from first correction to automatic behavior.

## 1. Start Fresh

Pick any project directory and initialize floop:

```bash
$ cd my-project/
$ floop init --project
Created .floop
Created .claude/settings.json

Ready! Your AI agents will now load learned behaviors at session start.
```

Nothing learned yet — floop is a blank slate:

```bash
$ floop list
No behaviors learned yet (local scope).

Use 'floop learn --right "Y"' to capture corrections.

$ floop active
Context:

Active behaviors (0):
```

## 2. The Mistake

You ask your AI agent to write a function that processes data from a file. It produces something like this:

```
function processFile(path):
    try:
        data = readFile(path)
        return transform(data)
    catch error:
        return null    // ← silently swallowed
```

The agent caught the error and returned `null` — no logging, no propagation. Callers have no idea something went wrong.

You correct it: *"Don't swallow errors silently — always log or propagate them."*

## 3. Capture the Correction

The agent captures the correction. Via **MCP** (recommended — your AI tool calls this automatically):

```
floop_learn(
    right="Always log errors or propagate them to the caller",
    wrong="Silently swallowed errors without logging or propagating"
)
```

Or equivalently via **CLI**:

```bash
$ floop learn \
    --right "Always log errors or propagate them to the caller" \
    --wrong "Silently swallowed errors without logging or propagating"
```

Either way, floop responds:

```
Correction captured and processed:
  Wrong: Silently swallowed errors without logging or propagating
  Right: Always log errors or propagate them to the caller

Extracted behavior:
  ID:   behavior-a1b2c3d4e5f6
  Name: learned/always-log-errors-or-propagate-them-to-the-caller
  Kind: directive
```

Verify it's stored:

```bash
$ floop list --all
Learned behaviors - all (local + glo

*[truncated — see source for full prompt]*