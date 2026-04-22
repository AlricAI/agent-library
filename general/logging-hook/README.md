# Logging Hook

> This script is a **GitHub Copilot event hook** that selectively logs agent-mode interactions (those involving tool use) while silently discarding pure question/answer sessions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How `logging-hook.sh` Works

This script is a **GitHub Copilot event hook** that selectively logs agent-mode interactions (those involving tool use) while silently discarding pure question/answer sessions.

---

## Core Concept: Buffered Logging

The key design challenge: you don't know upfront whether a session will use tools. The solution is **optimistic buffering** — events are held in `/tmp` files and only flushed to permanent logs when tool use is confirmed.

## Three File Sets

For each session (identified by `session_id` from the JSON payload), the script creates:

| File                            | Purpose                                                        |
| ------------------------------- | -------------------------------------------------------------- |
| `/tmp/copilot-hook-<id>.jsonl`  | Buffered JSONL events (pending)                                |
| `/tmp/copilot-hook-<id>.log`    | Buffered human-readable log (pending)                          |
| `/tmp/copilot-hook-<id>.active` | **Sentinel file** — its _existence_ means "tool use confirmed" |

The permanent destinations are date-stamped files in `logs/`:

- `YYYY-MM-DD-conversations.jsonl` — structured machine-readable log
- `YYYY-MM-DD.log` — human-readable log

---

## Event Flow

```
SESSIONSTART / USERPROMPTSUBMITTED
        │
        ▼
   .active exists? ──yes──► log directly to final files
        │ no
        ▼
   buffer to /tmp files

PRETOOLUSE ──► flush /tmp buffers → final files, create .active marker
              then log this event directly

POSTTOOLUSE / AGENTSTOP ──► log only if .active exists (tool session)

SESSIONEND ──► log if .active exists, then cleanup ALL /tmp files
```

If a session ends **without** `PRETOOLUSE` ever firing, the `/tmp` buffers are simply deleted — nothing reaches the permanent logs.

---

## The `append_event` Helper

Writes **two formats** simultaneously to the destination files:

1. **JSONL line** — a single JSON object with timestamp, event type

*[truncated — see source for full prompt]*