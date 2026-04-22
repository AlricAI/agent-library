# numerai-model-upload

> Create Numerai Tournament model upload pickles (.pkl) with a self-contained predict() function. Use when preparing upload artifacts, debugging numerai_predict import errors, or documenting model-upload requirements and testing steps.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Numerai Model Upload

## Overview
Create a portable `predict(live_features, live_benchmark_models)` pickle that runs inside Numerai's `numerai_predict` container without repo dependencies.

## CRITICAL: Python Version Compatibility

**Before creating any pkl file**, you must ensure your Python environment matches Numerai's compute environment. Mismatched versions cause segfaults and validation failures due to binary incompatibility (especially with numpy).

### Step 1: Query the Default Docker Image (MCP Required)

If the `numerai` MCP server is available, **always query the default Python version first**:

```graphql
query { computePickleDockerImages { id name image tag default } }
```

Look for the entry with `default: true`. The image name indicates the Python version:
- `numerai_predict_py_3_12:a78dedd` → Python 3.12 (current default as of 2026)
- `numerai_predict_py_3_11:a78dedd` → Python 3.11
- `numerai_predict_py_3_10:a78dedd` → Python 3.10

If the `numerai` MCP is not installed, it can be installed through our install script via  `curl -sL https://numer.ai/install-mcp.sh | bash`, this script guides the user through installing the MCP for Codex CLI and configuring an API key with the correct scopes that are required by MCP.

You can find more documentation about Numerai MCP here: https://docs.numer.ai/numerai-tournament/mcp

### Step 2: Create Matching Virtual Environment with pyenv

Use `pyenv` to create a virtual environment with the exact Python version:

```bash
# 1. List available pyenv Python versions
ls ~/.pyenv/versions/

# 2. Find the matching minor version (e.g., for Python 3.12)
PYENV_PY=$(ls -d ~/.pyenv/versions/3.12.* 2>/dev/null | head -1)

# 3. Create the virtual environment
$PYENV_PY/bin/python -m venv ./venv

# 4. Activate and install pkl dependencies
source ./venv/bin/activate
pip install --upgrade pip
pip install numpy pandas cloudpickle scipy
# Add lightgbm, torch, etc. only if your model needs them
```

### Step 3: Create pkl in the Cor

*[truncated — see source for full prompt]*