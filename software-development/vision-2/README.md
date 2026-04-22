# VISION

> Last updated: 2026-03-07

This document is the north star for CodeFRAME. It is not a roadmap, a spec, or a task list. It describes where the project i

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME Vision: Think, Build, Prove, Ship

Last updated: 2026-03-07

This document is the north star for CodeFRAME. It is not a roadmap, a spec, or a task list. It describes where the project is going and why. Tactical decisions should be evaluated against this vision.

---

## The Thesis

The IDE of the future is not a better text editor with AI autocomplete. It is a **project delivery system** where writing code is a subprocess.

Coding agents are getting remarkably good at writing code. Claude Code, Codex, OpenCode, Cursor, Kilocode -- these tools are backed by enormous engineering teams and frontier models, and they will keep getting better. Competing with them at the "write code" layer is a losing game.

But shipping software is not the same as writing code.

Before code gets written, someone has to figure out **what** to build, break it down into tasks an agent can execute, and resolve the ambiguities that would otherwise cause the agent to go off-scope. After code gets written, someone has to **verify** it actually works -- not just "tests pass" but "this provably meets requirements and hasn't broken anything we've already fixed."

Today, that "someone" is still you. CodeFRAME's purpose is to make it not you.

---

## The Pipeline

```
THINK -----> BUILD -----> PROVE -----> SHIP
  ^                                      |
  |                                      |
  +------ CLOSED LOOP (learn) <----------+
```

### THINK: What are you building?

Most software projects fail not because the code is bad, but because the *requirements* are bad. The spec is vague. The tasks are too big. The ambiguities aren't surfaced until an agent (or developer) is halfway through implementation and hits a wall.

CodeFRAME's THINK layer is a structured process for going from "I have an idea" to "here are atomic, executable tasks with dependencies":

1. **Socratic PRD generation** -- AI conducts a multi-turn discovery session, progressively refining from broad vision to specif

*[truncated — see source for full prompt]*