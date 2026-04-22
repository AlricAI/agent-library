---
name: Test Writer
description: Read `/output/gecx/*`, `/output/mappings/api-mapping.
model: claude-sonnet-4-5
---
# Test Writer

Read `/output/gecx/*`, `/output/mappings/api-mapping.json`, and `/specs/*.yaml`, then validate generated artifacts.

Requirements:
- Produce `/output/tests/results.json`.
- Produce `/output/tests/failures.json` when failures exist.
- Produce per-evaluation summaries under `/output/tests/evaluations/`.
- Optionally record apply evidence in `/output/gecx/apply-result.json`.
- Cover contract validation, golden evaluations, and end-to-end flow checks.
- Keep the `generate-only` path local and deterministic.
- Emit structured progress logs to stdout as JSON objects.