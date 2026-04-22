# AGENTS

> Goal: play the Numerai Tournament by running experiments and implementing new
research ideas to find models with strong BMC (Benchmark Model Contribut

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Numerai Agent

Goal: play the Numerai Tournament by running experiments and implementing new
research ideas to find models with strong BMC (Benchmark Model Contribution). The end goal
is a stable of relatively unique, high-performing models for submission.

Always check the agents/skills/ folder for skills that match the user request.
Run commands from `numerai/` (so `agents` is importable), or from repo root with `PYTHONPATH=numerai`.
Data is expected to live under `numerai/<data_version>/` (e.g. `numerai/v5.2/`), which is often gitignored locally.

To make these repo skills available to Codex CLI, symlink them into `~/.codex/skills/`:
`ln -s $PWD/numerai/agents/skills/* ~/.codex/skills/`

## Python Environment Setup

**IMPORTANT**: Before creating pkl files for upload, ensure your Python version matches Numerai's compute environment to avoid binary incompatibility errors (e.g., segfaults from numpy version mismatches).

```graphql
query { computePickleDockerImages { id name image tag default } }
```

Look for the image with `default: true` to determine the required Python version (e.g., `numerai_predict_py_3_12:a78dedd` means Python 3.12).

### Creating the Correct Virtual Environment

Use `pyenv` to create a virtual environment matching Numerai's Python version:

```bash
# 1. Check available pyenv versions
ls ~/.pyenv/versions/

# 2. Create venv with matching Python version (e.g., for Python 3.12)
~/.pyenv/versions/3.12.*/bin/python -m venv ./venv

# 3. Activate and install dependencies
source ./venv/bin/activate
pip install numpy pandas cloudpickle scipy lightgbm
```

When running code, look for a local virtual environment and activate it. Prefer the venv that matches the Numerai default Python version.

## Modeling philosophy
- All model-specific logic belongs in model configs and/or `agents/code/modeling/models/` wrappers.
- `pipeline.py`, `numerai_cv.py`, and metrics/analysis stay model-agnostic: they load requested data, call `fit`/`predict`, and record ou

*[truncated — see source for full prompt]*