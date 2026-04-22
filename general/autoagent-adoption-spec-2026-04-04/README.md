# Autoagent Adoption Spec 2026 04 04

> Last updated: 2026-04-04

## Goal

Adopt AutoAgent as an offline harness-optimization lab for a small set of narrow Blueprint automation lanes, withou

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AutoAgent Adoption Spec

Last updated: 2026-04-04

## Goal

Adopt AutoAgent as an offline harness-optimization lab for a small set of narrow Blueprint automation lanes, without replacing Hermes/Paperclip as the production operating system.

This spec assumes immediate implementation on the current repo and host, not a staged four-week planning exercise.

## Non-Goals

- Do not let AutoAgent mutate production employee agents directly.
- Do not replace Paperclip issue state, queue state, or human gates.
- Do not route production Hermes-backed agents through AutoAgent directly.
- Do not optimize payout, rights, legal, privacy, or other irreversible decision lanes first.

## First 3 Pilot Lanes

1. `waitlist_triage`
2. `support_triage`
3. `preview_diagnosis`

These are the best initial pilots because they already have:

- narrow structured inputs
- schema-bound outputs
- measurable end states
- lower business risk than payout or executive lanes

## Repo Shape

Use a repo-local lab scaffold now, then split to a standalone repo later if needed.

Recommended structure:

```text
labs/autoagent/
  README.md
  program.md
  tasks/
    README.md
    waitlist-triage/
      CASE_FORMAT.md
    support-triage/
      CASE_FORMAT.md
    preview-diagnosis/
      CASE_FORMAT.md
```

The current repo keeps:

- production task contracts in `server/agents/tasks/`
- production workflow execution in `server/agents/workflows.ts`
- shadow-run comparison storage under `ops_automation.shadow_runs.autoagent`

## Harbor Eval Format

Each historical case should become one Harbor task directory or one task fixture consumed by a lane-specific verifier.

Each case needs:

- `input.json`
  Exact production task input payload
- `expected.json`
  Human-accepted structured outcome
- `labels.json`
  Risk weights and review expectations

Example common fields:

```json
{
  "case_id": "waitlist-2026-03-14-001",
  "lane": "waitlist_triage",
  "input": {},
  "expected": {},
  "labels": {
    "requires_human

*[truncated — see source for full prompt]*