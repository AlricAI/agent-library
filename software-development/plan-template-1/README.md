# PLAN TEMPLATE

> > **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# [Feature Name] Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

<!-- Goal: One sentence describing the user-facing outcome — what someone can do
     after this change that they could not do before. -->
**Goal:** [1-2 sentences: what someone can do after this change that they could not do before]

**Spec:** `docs/superpowers/specs/YYYY-MM-DD-<topic>-design.md`

**Existing code:** [Key files and modules this plan touches]

---

## Purpose / Big Picture

<!-- Describe what someone gains after this change and how they can verify it.
     Keep this user-visible and outcome-oriented. -->

[What will exist after this lands, and how someone can observe it working.]

---

## Context and Orientation

<!-- Orient the next contributor quickly. Link the important docs, point at the
     code hotspots, and spell out any constraints they need before editing. -->

- **Docs to read:** `docs/...`
- **Primary files:** `path/to/file.py`, `path/to/other.py`
- **Constraints:** [Architecture, rollout, or safety constraints]

---

## Milestones

<!-- Milestones are narrative checkpoints. Each should be independently
     verifiable and explain what new thing exists at the end. -->

1. **Milestone 1:** [Scope, expected proof, and verification command]
2. **Milestone 2:** [Scope, expected proof, and verification command]

---

## Progress

<!-- Granular status tracker. Update timestamps as work proceeds so anyone can
     see at a glance what is done and what remains. -->

| Step | Status | Updated |
|------|--------|---------|
| Chunk 1 / Task 1 | Not started | |
| ... | | |

---

## File Structure

### New files:
- `path/to/new_file.py` — brief purpose

### Modified files:
- `path/to/existing.py` — what changes

---

## Chunks & Tasks

<!-- Organize as Chunk (theme) → Task (unit of work) → Steps (checkboxe

*[truncated — see source for full prompt]*