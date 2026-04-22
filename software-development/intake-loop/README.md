# Intake Loop

> How the intake phase gathers context in three steps, and the prompt
engineering principles that govern it.

> Parent doc: [architecture.md](./architec

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Intake Phase Design

How the intake phase gathers context in three steps, and the prompt
engineering principles that govern it.

> Parent doc: [architecture.md](./architecture.md)
> Related: [subagents.md -- Step-First Workflow](./subagents.md#step-first-workflow)

---

## Overview

The intake phase is the most consequential phase in the pipeline. Its
output -- verified understanding of the task and codebase -- is the foundation
for all downstream phases. Every implementation plan and every line of code
produced downstream depends on the completeness and accuracy of what intake
discovers. Gaps compound: a missed decision becomes a wrong plan becomes
wrong code.

The intake phase runs a focused **three-step workflow**: gather context
(conversation + codebase orientation + scouts), deepen understanding through
dialogue and codebase verification, then synthesize findings into a handoff
summary.

### Step structure

| Step | Name      | Runs | Purpose                                                                  |
| ---- | --------- | ---- | ------------------------------------------------------------------------ |
| 1    | Gather    | 1x   | Read conversation, open obvious files (<=5), dispatch scouts.            |
| 2    | Deepen    | 1x   | Process scout results, verify by reading files, deepen through dialogue. |
| 3    | Summarize | 1x   | Synthesize findings into a concise handoff summary.                      |

All steps advance linearly. The phase boundary after step 3 gives the user a
natural point to review the summary and discuss next steps.

---

## Step Design

### Step 1: Gather

The Gather step combines what was previously three separate activities
(reading the conversation, orienting in the codebase, and dispatching scouts)
into a single `koan_complete_step` cycle. This avoids the latency and context
re-derivation overhead of artificially separating them.

The step has a **5-file budget** for initial exploration: project root listing,
orientation f

*[truncated — see source for full prompt]*