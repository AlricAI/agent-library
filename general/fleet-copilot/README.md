# FLEET COPILOT

> The fleet co-pilot merges lock mode with SessionCopilot reasoning into a single
feature. When you tell Claude to work autonomously, it formulates a go

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fleet Co-Pilot — Autonomous Lock Mode

The fleet co-pilot merges lock mode with SessionCopilot reasoning into a single
feature. When you tell Claude to work autonomously, it formulates a goal,
enables lock mode, and uses LLM reasoning to stay on track until the goal is
achieved.

## Quick Start

Tell Claude what you want done using natural language:

```
/amplihack:lock fix the auth bug, make sure all tests pass, then create a PR
```

Or use the fleet-copilot skill:

```
/fleet-copilot implement OAuth2 login with PKCE flow and add integration tests
```

Claude will:

1. Formulate a goal and definition of done from your words
2. Write the goal to `.claude/runtime/locks/.lock_goal`
3. Enable lock mode
4. Start working immediately

## CLI Commands

### fleet setup

Check prerequisites and install azlin if missing. Run on a new machine:

```
fleet setup
```

### fleet copilot-status

Show whether the co-pilot is active, the current goal, and lock state:

```
fleet copilot-status
```

### fleet copilot-log

View the co-pilot's decision history (what it decided and why):

```
fleet copilot-log
fleet copilot-log --tail 5     # last 5 decisions
```

## How It Works

Two hooks work together:

### LockModeHook (provider:request)

Injects the goal as a system directive on every LLM call so the agent always
has context about what it's working toward. Passive — no reasoning here.

### Stop Hook (on stop)

When the agent tries to stop, the Stop hook:

1. Reads the goal file
2. Calls `SessionCopilot.suggest()` which:
   - Reads the full session transcript
   - Builds rich context (first user message + summarized middle + recent entries)
   - Reasons about progress toward the goal
3. Based on the suggestion:
   - **send_input** (confidence >= 0.6): Blocks stop with specific next-step guidance
   - **wait**: Blocks stop with a generic "keep working toward goal" prompt
   - **mark_complete**: Auto-disables lock, tells agent to summarize completed work
   - **escalate**: Auto-disabl

*[truncated — see source for full prompt]*