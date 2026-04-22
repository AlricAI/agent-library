# ANALYTICS SPEC

> **Project**: Life Tracker
**Version**: 2.0 (Event-Driven Architecture)
**Date**: 2026-01-14
**Status**: Design Proposal

---

## Table of Contents

1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Analytics Specification

**Project**: Life Tracker
**Version**: 2.0 (Event-Driven Architecture)
**Date**: 2026-01-14
**Status**: Design Proposal

---

## Table of Contents

1. [Philosophy & Goals](#philosophy--goals)
2. [Event Taxonomy](#event-taxonomy)
3. [Canonical Event List](#canonical-event-list)
4. [Event Properties Schema](#event-properties-schema)
5. [Privacy & Security Rules](#privacy--security-rules)
6. [Questions We Can Answer](#questions-we-can-answer)
7. [Implementation Guide](#implementation-guide)

---

## Philosophy & Goals

### North Star Principle
**"ORE REALI FATTE" (Real Hours Done) - Track actual time spent, not just planned time.**

From CLAUDE.md:
> La metrica primaria è: ORE REALI FATTE (actual), non ore pianificate.

### Analytics Goals
1. **Understand user behavior** - What features drive value?
2. **Measure goal progress** - Is the hierarchical rollup working?
3. **Optimize retention** - Why do users return (or churn)?
4. **Validate product hypotheses** - Does auto-scheduler increase completion rate?
5. **Detect issues early** - Error rates, performance regressions

### Design Principles
- **Privacy-first**: No sensitive user data in events
- **Type-safe**: Compile-time event validation
- **Minimal**: Track only what's actionable
- **Deterministic**: Same action = same event
- **Fast**: Zero impact on user experience (async, batched)

---

## Event Taxonomy

### Naming Convention: `snake_case`

**Format**: `<object>_<action>`

Examples:
- `timeblock_created`
- `goal_completed`
- `scheduler_run`
- `error_occurred`

### Event Categories

| Category | Description | Examples |
|----------|-------------|----------|
| **Lifecycle** | User journey milestones | `user_signed_up`, `onboarding_completed` |
| **Core Actions** | Primary user interactions | `timeblock_completed`, `task_created` |
| **Feature Usage** | Specific feature adoption | `scheduler_run`, `analytics_viewed` |
| **Engagement** | Retention signals | `daily_login`, `streak_achieve

*[truncated — see source for full prompt]*