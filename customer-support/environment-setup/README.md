# Environment Setup

> ## Overview

This repository contains a rule-based Python prompt generator that uses only the
standard library. It supports an interactive numbered se

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
3. Run `python3 -m unittest tests/test_prompt_gene

*[truncated — see source for full prompt]*