# Json Logging

> ## Overview

Auto-mode now includes structured JSONL (JSON Lines) logging alongside the existing text logs. This provides machine-readable event data 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Structured JSON Logging for Auto-Mode

## Overview

Auto-mode now includes structured JSONL (JSON Lines) logging alongside the existing text logs. This provides machine-readable event data for programmatic analysis, monitoring, and debugging.

## Log File Location

The structured log is written to:

```
.claude/runtime/logs/<session_id>/auto.jsonl
```

Where `<session_id>` is the unique identifier for the auto-mode session (e.g., `auto_claude_1234567890`).

## Event Schema

Each line in `auto.jsonl` is a standalone JSON object with the following base structure:

```json
{
  "timestamp": "2026-01-20T00:14:09.680139+00:00",
  "level": "INFO",
  "event": "turn_start",
  ...additional fields...
}
```

### Common Fields

- `timestamp`: ISO 8601 formatted timestamp with timezone (UTC)
- `level`: Log level (`INFO`, `WARNING`, `ERROR`)
- `event`: Event type (see Event Types below)

### Event Types

#### 1. `turn_start`

Logged at the beginning of each turn.

```json
{
  "timestamp": "2026-01-20T00:14:09.680139+00:00",
  "level": "INFO",
  "event": "turn_start",
  "turn": 1,
  "phase": "clarifying",
  "max_turns": 20
}
```

**Fields:**

- `turn`: Current turn number (1-indexed)
- `phase`: Current phase (`clarifying`, `planning`, `executing`, `evaluating`, `summarizing`)
- `max_turns`: Maximum turns configured for the session

#### 2. `turn_complete`

Logged when a turn finishes execution.

```json
{
  "timestamp": "2026-01-20T00:14:11.815309+00:00",
  "level": "INFO",
  "event": "turn_complete",
  "turn": 1,
  "duration_sec": 23.42,
  "success": true
}
```

**Fields:**

- `turn`: Turn number that completed
- `duration_sec`: Duration of the turn in seconds (rounded to 2 decimal places)
- `success`: Boolean indicating if the turn succeeded (exit code 0)

#### 3. `agent_invoked`

Logged when an agent or tool is invoked during execution.

```json
{
  "timestamp": "2026-01-20T00:15:32.480478+00:00",
  "level": "INFO",
  "event": "agent_invoked",
  "agent": "TodoWrite",
  "turn"

*[truncated — see source for full prompt]*