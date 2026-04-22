---
name: Environment Setup
description: ## Overview

This repository contains a rule-based Python prompt generator that uses only the
standard library. It supports an interactive numbered se
model: claude-sonnet-4-5
---
# Environment Setup

## Overview

This repository contains a rule-based Python prompt generator that uses only the
standard library. It supports an interactive numbered selection workflow for
the current MVP, which starts with model selection and ends with a generic
placeholder scaffold.

## Requirements

- Python 3.11 or newer recommended
- No external packages required
- No API keys required
- No network access required for local validation
- Ubuntu/WSL may also require the system package `python3.12-venv` to create `.venv`

## Repository Layout

- `Agents.md`: workflow and role definitions
- `Project Management & Sprint Tracker.md`: sprint plan and status
- `candidate_rules.md`: deterministic rule source
- `prompt_generator.py`: single-file generator implementation
- `requirements.txt`: assignment-required dependency manifest
- `assignment_2_3_deliverables.md`: grading-ready deliverables document
- `tests/test_log.txt`: manual validation notes
- `tests/fixtures/`: accepted and rejected sample inputs for verification

## Branch Workflow

- Do active implementation work on `dev`
- Run verification on `dev`
- Promote to `main` only after the sprint checklist and verification commands pass

## Virtual Environment Setup

Create and activate a local virtual environment with:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

If `python3 -m venv .venv` fails on Ubuntu/WSL with an `ensurepip` error, install the missing system package first:

```bash
sudo apt-get update
sudo apt-get install -y python3.12-venv
```

Then recreate and activate the environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Once activated, verify with:

```bash
python -m py_compile prompt_generator.py
python -m unittest tests/test_prompt_generator.py
python prompt_generator.py --interactive
```

## Local Validation Steps

1. Confirm the required project files exist.
2. Run `python3 -m py_compile prompt_generator.py`.
3. Run `python3 -m unittest tests/test_prompt_generator.py`.
4. Run `python3 prompt_generator.py --interactive`.
5. Confirm the first prompt is exactly `What model are you choosing?`
6. Confirm the menus proceed in this order: model -> purpose -> role family -> experience level -> tone -> output format.
7. Enter one numeric selection per menu and verify invalid numeric input re-prompts the current menu instead of advancing.
8. Confirm the script asks for the general summary only after the output-format selection.
9. Confirm the final output is a plain-text placeholder scaffold that includes the selected model, selected category combination, and general summary.
10. Record observations in `tests/test_log.txt` when the active action item scopes validation-log updates.

## Not In Scope

- Machine learning logic
- External integrations
- Third-party libraries
- Packaging or deployment steps