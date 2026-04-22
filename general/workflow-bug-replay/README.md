# WORKFLOW BUG REPLAY

> This guide defines the minimum replay artifact and bug-fix loop for workflow-runtime failures.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Workflow Bug Replay Guide

This guide defines the minimum replay artifact and bug-fix loop for workflow-runtime failures.

Use it when:

- a live workflow blocks unexpectedly
- a workflow-runtime fix changes prompting, validation, repair, delivery, or status projection
- a release candidate includes workflow contract changes

## Policy

A workflow-runtime bug fix is not complete until a deterministic replay regression exists.

That replay must preserve the contract class of the live failure, not just the surface wording of one workflow.

## Minimum Replay Fixture

Capture these fields from the live blocker:

- automation ID
- run ID
- node ID
- node objective
- output contract kind
- required output path
- required workspace files, if any
- offered tools
- executed tools
- unmet requirements
- blocker category
- validator summary or blocker reason
- whether web research was used
- whether workspace inspection was used
- any upstream artifact paths or handoffs that materially affected the node

If the failure involved retries or repair:

- previous attempt count
- whether repair budget remained
- previous validation outcome
- required next tool actions

## Replay Template

Use this template when turning a live blocker into a regression:

```text
Live blocker:
- node_id:
- contract_kind:
- required_output_path:
- required_workspace_files:
- blocker_category:
- unmet_requirements:
- offered_tools:
- executed_tools:
- workspace_inspection_used:
- web_research_used:
- upstream_artifact_paths:
- validator_summary:
- repair_state:

Expected replay assertions:
- validation_outcome:
- final node status:
- failure kind / blocker category:
- required next actions:
- required unmet requirements that must remain visible:
```

## What The Replay Must Prove

At minimum, assert the bug class we care about:

1. The runtime preserves the right unmet requirements.
2. The node status and blocker category match the repairability of the failure.
3. Required next actions point the model

*[truncated — see source for full prompt]*