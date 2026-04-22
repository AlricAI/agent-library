# Todo

> Multi-session task list.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Livewire — Open Tasks & Ideas

Multi-session task list. Check and update at session start and end.
Each entry should carry enough context for a fresh agent to resume without asking.

---

_Last updated: 2026-03-21_

## 🚧 In Progress

### `trace` namespace — `hibernate-stats`

- **`(trace/hibernate-stats)`** — Snapshot of Hibernate's `Statistics` object:
  cache hit/miss ratios, entity load counts, collection fetch counts, slow queries.

---

## 🔜 Planned

### `query` namespace — SQL tracing inside `diff-entity`

Investigate whether wrapping `diff-entity` in `trace/trace-sql` captures the UPDATE/INSERT
statements that Hibernate fires on the explicit `.flush` call inside `in-tx`.

Two constraints to verify:
1. `trace/trace-sql` uses a `StatementInspector` — does it intercept write statements, or
   only SELECTs?
2. Hibernate's write-behind (dirty checking) means the UPDATE only fires on flush. `diff-entity`
   already calls `.flush em` explicitly before the after-snapshot, so the UPDATE *should* fire —
   but whether it is captured by `StatementInspector` before the rollback needs confirming.

If it works, the composition `(trace/trace-sql (q/diff-entity ...))` would give both the
entity diff *and* the SQL shape of the write in one call — a natural complement to the
existing read-side tracing story. Worth documenting in SKILL.md if confirmed.

---

### ~~faker support — Phase 0: extend `introspect` with `@Column` annotation metadata~~

✅ Done — `:nullable`, `:length`, `:unique`, `:column-definition` added to `inspect-entity` via reflection. Committed in `711c1f5`.

<!--

**Context:** The Hibernate runtime metamodel does not expose `nullable`, `length`, `unique`, or
`columnDefinition`. These are needed by the faker heuristic generator to produce valid entities
without hitting DB constraint violations. This is a prerequisite for Phase 1.

**What to do:**
- Extend `inspect-entity` (and `inspect-all-entities`) to walk entity class fields/methods via
  Java reflection,

*[truncated — see source for full prompt]*