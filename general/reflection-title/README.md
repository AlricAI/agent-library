# Reflection Title

> ## Overview

The **reflection-title** task automatically generates creative, emoji-enriched
titles for daily reflection notes in the Obsidian vault. I

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Reflection Title Generation

## Overview

The **reflection-title** task automatically generates creative, emoji-enriched
titles for daily reflection notes in the Obsidian vault. It runs at or after
10 PM Pacific time each day, after all blog posts and content have been added
to the daily reflection.

## Architecture

| Component | Path |
|-----------|------|
| Library | `haskell/src/Automation/ReflectionTitle.hs` |
| Tests | `haskell/test/Automation/ReflectionTitleTest.hs` |
| Scheduler entry | `haskell/src/Automation/Scheduler.hs` (`reflection-title`, hour 22 Pacific) |
| Orchestrator runner | `haskell/app/RunScheduled.hs` (`runReflectionTitle`) |

## Schedule

- **Hour**: 22 Pacific (10 PM PST / PDT)
- **Semantics**: At-or-after — eligible at hour 22 and all subsequent hours
  (in Pacific time) until 11:59 PM Pacific
- **Catchup**: Also titles yesterday's reflection if it's still untitled
- **Idempotency**: Skips if the title field already contains a creative title
  (i.e., anything beyond the bare date)

## Title Format

Titles follow a creative game observed across 20+ existing reflection notes:

```
YYYY-MM-DD | 🕊️ Gentle 🚪 Constraint 🏛️ Commons 📚🐔🤖🏛️📺
```

### The "One Word Per Title" Game

1. **Extract linked content titles** — deterministically pull titles of books,
   blog posts, videos, etc. from list items in the reflection note, excluding
   list items from the Updates section
2. **Strip prefixes** — remove date prefixes and emoji prefixes from titles
3. **AI structured sentence building** — Gemini follows a multi-step process
   that defers word selection to avoid premature commitment:
   a. Build a full word inventory — label ALL words in ALL titles with parts of speech
   b. Draft 2–3 grammatical sentence templates using only POS labels (no actual words yet)
   c. Fill templates from the full inventory, trying multiple word combinations (one word per title)
   d. Compare candidates and iterate until a coherent, evocative phrase emerges
   e.

*[truncated — see source for full prompt]*