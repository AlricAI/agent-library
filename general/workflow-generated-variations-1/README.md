# WORKFLOW GENERATED VARIATIONS

> This document defines the constrained generator strategy for workflow-runtime coverage.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Workflow Generated Variation Coverage

This document defines the constrained generator strategy for workflow-runtime coverage.

The goal is not to model every possible workflow. The goal is to generate representative node and workflow shapes that stress the runtime contracts we care about.

## Why This Exists

Deterministic replay tests and archetype integrations catch known failures well, but they cannot cover the full space of workflow variation on their own.

Generated variation coverage gives us a third layer:

- broader spec coverage than hand-written archetypes
- more stable signal than unconstrained fuzzing
- a safe nightly lane before anything becomes release-blocking

## Constraints

Generated cases must stay:

- deterministic
- small enough to run repeatedly in CI
- interpretable when a failure occurs
- tied to engine contracts, not product-specific workflow names

Avoid:

- random external dependencies
- open-ended fuzzing in blocking CI
- giant snapshots that are hard to debug

## Phase 1 Generator Shape

Start with a bounded grammar over node contracts:

- output contract kind:
  - `structured_json`
  - `brief`
  - `citations`
  - `report_markdown`
  - `approval_gate`
- evidence mode:
  - local
  - MCP
  - web
  - mixed
- write pattern:
  - artifact only
  - artifact plus required workspace files
- special behavior:
  - filesystem bootstrap
  - synthesis with upstream evidence
  - delivery
  - code verification

The first generated suite should stay prompt- and contract-focused:

- does the prompt include the right required output instructions?
- does MCP-backed work include `mcp_list` discovery guidance?
- do filesystem-only nodes avoid web-research instructions?
- do code-change nodes include verification and patch/edit guidance?

## Later Expansion

After the prompt-variation suite is stable, add generated cases for:

1. validation outcome invariants
2. repairability vs blocked routing
3. delivery side-effect classification
4. upstream evidence pre

*[truncated — see source for full prompt]*