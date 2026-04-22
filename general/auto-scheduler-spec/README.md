# AUTO SCHEDULER SPEC

> **Project**: Life Tracker
**Version**: 2.0 (Deterministic, Timezone-Aware, Explainable)
**Date**: 2026-01-14
**Status**: Design Proposal

---

## Tabl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Auto-Scheduler Specification

**Project**: Life Tracker
**Version**: 2.0 (Deterministic, Timezone-Aware, Explainable)
**Date**: 2026-01-14
**Status**: Design Proposal

---

## Table of Contents

1. [Core Principles & Invariants](#core-principles--invariants)
2. [Architecture](#architecture)
3. [Scheduling Algorithm](#scheduling-algorithm)
4. [Timezone Handling](#timezone-handling)
5. [Conflict Resolution](#conflict-resolution)
6. [Explainability](#explainability)
7. [Edge Cases](#edge-cases)
8. [Testing Strategy](#testing-strategy)
9. [Performance Requirements](#performance-requirements)

---

## Core Principles & Invariants

### Non-Negotiable Invariants

#### 1. Determinism
**Same inputs → Same outputs**

```typescript
// MUST always produce identical schedule for identical inputs
const result1 = schedule(tasks, constraints, timezone, seed);
const result2 = schedule(tasks, constraints, timezone, seed);
assert(deepEqual(result1, result2));
```

**Implementation**:
- No `Date.now()` inside algorithm - use `constraints.currentTime`
- No `Math.random()` - use seeded PRNG
- Sort all arrays before iteration (stable ordering)

#### 2. Idempotency
**Repeated runs don't duplicate blocks**

```typescript
// Run twice with same inputs
schedule(tasks, constraints);
schedule(tasks, constraints);

// Should NOT create duplicate blocks
const blocks = await db.getAll('timeBlocks');
const autoblocks = blocks.filter(b => b.id.startsWith('auto-scheduled-'));
assert(autoblocks.length === expectedCount); // Not 2x
```

**Implementation**:
- Deterministic IDs: `auto-scheduled-${taskId}-${slotStart}-${date}`
- Deduplication check before creating blocks
- "Upsert" semantics - update if exists, create if not

#### 3. Timezone Correctness
**"9 AM" means 9 AM in user's timezone**

```typescript
// User in PST (UTC-8)
const slot = findSlot(task, { timezone: 'America/Los_Angeles', hour: 9 });

// Slot.startTime MUST be 9:00 AM PST (17:00 UTC)
assert(slot.startTime.toLocaleString('en-US', { 

*[truncated — see source for full prompt]*