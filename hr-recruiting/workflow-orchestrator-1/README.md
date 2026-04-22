# Workflow Orchestrator

> ## Problem Statement

Koan's pipeline manages an epic through eight phases:

```
intake → brief-generation → core-flows → tech-plan → ticket-breakdown

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Workflow Orchestrator — Implementation Plan

## Problem Statement

Koan's pipeline manages an epic through eight phases:

```
intake → brief-generation → core-flows → tech-plan → ticket-breakdown
→ cross-artifact-validation → execution → implementation-validation
```

Only **intake** and **brief-generation** are currently implemented. The
remaining six phases exist as stubs — placeholder registrations in the phase
DAG that auto-advance when reached. Every run traverses every phase in exactly
this order. This creates two concrete problems.

**First, no flexibility.** A user who already understands the problem space
cannot skip brief generation. A user who wants to jump directly to core-flow
definition — bypassing the brief — has no way to express that intent. Adding
successor branches between phases would require forking the pipeline or adding
a tangle of conditional flags — both are maintenance traps.

**Second, no handoff.** When a phase completes, the pipeline silently advances.
The user sees no summary of what was accomplished, no explanation of what the
next phase will do, and no opportunity to adjust focus before work begins. This
matters most when phases accumulate context: after intake, the orchestrator
knows what was discussed; the next phase's LLM does not, unless context is
explicitly passed forward.

This plan replaces the hardcoded sequence with a **user-directed, orchestrator-
mediated loop**. After each phase completes, a workflow orchestrator agent
evaluates what was produced, surfaces a contextual status report with
recommended next phases, and holds a multi-turn conversation with the user to
agree on direction — with optional instructions that shape what the next phase
does. The orchestrator session appears inline in the ActivityFeed as a
continuation of the completed phase's activity, preserving full visual
continuity.

---

## Breaking Changes

This plan is a **breaking change** for existing epic directories. The
`EpicPhase` type renames `"brief

*[truncated — see source for full prompt]*