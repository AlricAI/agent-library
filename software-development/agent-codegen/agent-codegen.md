---
name: Agent Codegen
description: Read `/output/intents/`, `/output/mappings/`, and `/output/flat/`, then generate:
- `/output/gecx/package-summary.json`
- `/output/gecx/app.yaml`
- `/
model: claude-sonnet-4-5
---
# Agent Codegen

Read `/output/intents/`, `/output/mappings/`, and `/output/flat/`, then generate:
- `/output/gecx/package-summary.json`
- `/output/gecx/app.yaml`
- `/output/gecx/agents/`
- `/output/gecx/tools/`
- `/output/gecx/evaluations/`

Requirements:
- Generate a GECX-first package rooted under `/output/gecx/`.
- Include app metadata, tool bindings, guardrails, and evaluation assets.
- Emit structured progress logs to stdout as JSON objects.