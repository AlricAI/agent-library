# REFACTORING ROADMAP SOLID

> This document complements `[ARCHITECTURE.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Refactoring roadmap — concerns, SOLID, and dumb components

This document complements `[ARCHITECTURE.md](./ARCHITECTURE.md)` and `[CLAUDE.md](../CLAUDE.md)`. Use it when planning tickets (e.g. **T-015h** delete flows) so new code does not lock in the wrong shape, and to prioritize later cleanups.

---

## How to use this doc

1. **Before a feature** — skim the relevant area (Feed, Spaces, Wiki, Server). Note what to extract *alongside* the feature vs what to defer.
2. **During implementation** — prefer **thin routes/screens**, **hooks for orchestration**, **presentational components with props in**.
3. **After a milestone** — pick one “hot” file from the tables below; refactor in a dedicated ticket so behavior stays testable.

---

## SOLID — practical mapping for this repo


| Principle                 | What it means here                                                                                                   | Smell                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **S**ingle responsibility | One file answers one question: “layout”, “fetch”, “map API → UI model”, or “render”.                                 | Screen does query + 5 `useMemo` + error UI + list + modal.   |
| **O**pen/closed           | Extend via variants (`tv`), new hooks, or new small components — not by growing one mega-component.                  | Every new feed action edits `FeedScreen` only.               |
| **L**iskov                | N/A for most UI; relevant for shared abstractions (e.g. list row props contracts).                                   | Optional row props that sometimes need fetch inside the row. |
| **I**nterface segregation | Presentational pieces take **narrow props** (`onPress`, `title`, `isLoading`) — not whole query results or `router`. | Pa

*[truncated — see source for full prompt]*