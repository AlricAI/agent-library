# Memory Systems

> > Every session should make the next one better.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory Systems

> Every session should make the next one better.

## The Problem

You explain the same thing to the AI every Monday. "We use trunk-based development." "The auth middleware is in this file." "Don't mock the database in integration tests." Without persistent memory, every session starts from zero.

## The Pattern

### Three Layers of Memory

```
┌─────────────────────────────────────────────┐
│  Layer 1: Static Context (always loaded)    │
│  CLAUDE.md, .cursorrules, AGENTS.md         │
│  → Project rules, architecture, commands    │
├─────────────────────────────────────────────┤
│  Layer 2: Dynamic Memory (loaded on demand) │
│  Memory files, learned patterns, decisions  │
│  → What was done, why, what to avoid        │
├─────────────────────────────────────────────┤
│  Layer 3: Session State (ephemeral)         │
│  Conversation history, current task context │
│  → Discarded after session ends             │
└─────────────────────────────────────────────┘
```

### What to Remember

| Memory Type | Example | Where to Store |
|-------------|---------|---------------|
| **User preferences** | "Never add co-authored-by to commits" | Global memory |
| **Feedback** | "Don't mock the DB — we got burned last quarter" | Project memory |
| **Decisions** | "We chose Supabase over Firebase because of row-level security" | Project memory |
| **References** | "Pipeline bugs are tracked in Linear project INGEST" | Project memory |
| **Gotchas** | "pre-commit runs full monorepo type-check, use HUSKY=0 for docs" | Project rules file |

### What NOT to Remember

- Code patterns (read from the current codebase)
- Git history (use `git log` / `git blame`)
- Debugging solutions (the fix is in the code, the context is in the commit)
- Ephemeral task details (current session handles these)

### Memory File Structure

```
.claude/memory/          # or .serena/memories/, .cursor/context/
  MEMORY.md              ← Index file (always loaded, kept short)
  user-preferences.m

*[truncated — see source for full prompt]*