# Olivia Implementation Plan

> ## When To Use

Use this when an approved or sufficiently concrete feature spec needs to become an execution-ready implementation plan for an engineer

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Olivia Implementation Plan Writer

## When To Use

Use this when an approved or sufficiently concrete feature spec needs to become an execution-ready implementation plan for an engineering agent.

## Goal

Turn durable product guidance into a step-by-step plan that is explicit about scope, sequencing, verification, and evidence without re-deciding the product.

## Inputs

- The target feature spec
- The intended plan file path, if one has already been chosen

## Steps

### 1. Load the source artifacts

Read:

1. the target feature spec
2. `docs/vision/product-vision.md`
3. `docs/vision/product-ethos.md`
4. `docs/roadmap/milestones.md`
5. `docs/learnings/decision-history.md`
6. `docs/learnings/assumptions-log.md`
7. any related learnings or specs referenced by the target spec

### 2. Confirm planning readiness

Before drafting the plan, confirm:

- the project is at M3 or the user explicitly wants early planning
- the spec is concrete enough to implement without major product ambiguity
- any remaining open questions are bounded and non-blocking, or are called out explicitly as blockers

If those conditions are not met, do not hide the ambiguity inside the engineering plan. Surface the blocker first.

### 3. Draft the implementation plan

Create or update the requested plan file. If no path is specified, prefer a clearly named markdown file in a planning area already used by the repo; if none exists, use a path the user asks for.

Include these sections:

- **Summary:** what will be built and why
- **Source Artifacts:** the exact docs and specs the plan derives from
- **Assumptions And Non-Goals:** any bounded assumptions plus the work that is explicitly out of scope
- **Implementation Steps:** ordered work items that an agent can execute without guessing the goal
- **Verification:** tests, manual checks, or household validation required
- **Evidence Required:** what artifacts or outputs prove each major step succeeded
- **Risks / Open Questions:** only the i

*[truncated — see source for full prompt]*