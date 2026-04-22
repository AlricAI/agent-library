# Scenario 11 Output Gates

> **Pattern:** `output-gate`
**Tests:** Sub-agents with an `## Output Gate` section emit a hallucination-proof bash gate in the dispatch manifest; the o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario 11: Output Gates (Bash Validation)

**Pattern:** `output-gate`
**Tests:** Sub-agents with an `## Output Gate` section emit a hallucination-proof bash gate in the dispatch manifest; the orchestrator is instructed to run it and trust stdout over self-reports.

---

## Goal

Validate that `dispatch_agent_team.py`:

1. Parses the optional `## Output Gate` section from a sub-agent directive
2. Emits a `validation_gate` entry in the manifest with a bash command that prints `VALIDATION:PASS` or `VALIDATION:FAIL:<path>`
3. Resolves `{{run_id}}` and `{{payload.<key>}}` placeholders
4. Updates the orchestrator instructions to mandate running the gate before advancing

This closes a known failure mode: LLM orchestrators fabricate success reports when sub-agents produce empty or missing outputs. The gate is deterministic bash — no LLM judgment, no hallucination surface.

---

## What This Tests

| Test Point | Expected |
|---|---|
| Directive without `## Output Gate` | Manifest entry has NO `validation_gate` key |
| Directive with `## Output Gate` | Manifest entry has `validation_gate.command` + `output_files` + `on_fail` |
| Placeholder substitution | `{{run_id}}` and `{{payload.key}}` resolved in `output_files` |
| Gate command (PASS) | `bash -c "<command>"` exits 0 and prints `VALIDATION:PASS` when file exists |
| Gate command (FAIL) | `bash -c "<command>"` exits 1 and prints `VALIDATION:FAIL:<path>` when file missing |
| Orchestrator instructions | Reference `validation_gate.command`, "VALIDATION:PASS", retry-once-then-user pattern |

---

## Run

```bash
# Sequential dispatch using the documentation_team (changelog-updater declares a gate)
python3 execution/dispatch_agent_team.py \
  --team documentation_team \
  --payload '{"changed_files":["execution/dispatch_agent_team.py"],"commit_msg":"test","change_type":"test"}' \
  --dry-run | python3 -c "
import json, sys, subprocess
m = json.load(sys.stdin)
gated = [sa for sa in m['sub_agents'] if 'validation_gate' in 

*[truncated — see source for full prompt]*