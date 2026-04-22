# NORTH STAR

> Tandem is becoming a durable runtime for autonomous work.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem North Star

Tandem is becoming a durable runtime for autonomous work.

The goal is not to build another chat assistant, IDE wrapper, or transcript-driven agent shell. The goal is to build the system of record for long-running work across coding, research, writing, publishing, and recurring automation.

Chat will remain a useful interface. It will not be the source of truth.

The source of truth should be the engine: runs, tasks, blackboards, checkpoints, artifacts, validations, approvals, receipts, and replayable event history.

---

## Why Tandem Exists

Most agent products still treat the conversation as the runtime.

That is good enough for short demos. It breaks down under real work.

When the transcript is doing too much, systems become fragile:

- long-running tasks lose context
- retries behave inconsistently
- failures are hard to audit
- resume behavior is weak
- parallel agents collide or duplicate work
- tool calls are not durable enough
- non-coding workflows get bolted on as separate systems

Tandem exists to solve that problem.

We believe autonomous execution is fundamentally a systems problem, not a chat problem.

---

## What Tandem Is Becoming

Tandem is becoming a unified runtime for autonomous work with:

- engine-owned state instead of transcript-owned state
- blackboard-based coordination instead of ad hoc memory sharing
- one canonical run journal for lineage, replay, and recovery
- isolated execution scopes for safe parallel work
- runtime-owned artifacts, validations, and approvals
- approval-aware external actions with durable receipts
- one shared execution model across multiple domains

The intended outcome is a system that can:

- inspect context
- form a plan
- break work into tasks
- delegate execution
- coordinate through blackboards
- validate outputs
- recover from failure
- resume safely
- operate continuously over time

---

## Product Direction

Tandem should become three things at once.

### A durable autonomous coding 

*[truncated — see source for full prompt]*