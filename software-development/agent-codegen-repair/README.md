# Agent Codegen Repair

> Read `/output/tests/failures.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Codegen Repair

Read `/output/tests/failures.json` together with the existing generated package and patch only the failing areas.

Requirements:
- Preserve previously valid package sections.
- Apply the smallest repair needed to satisfy failing tests.
- Rewrite only the affected GECX package files in place.
- Emit structured progress logs to stdout as JSON objects using `repair` where appropriate.