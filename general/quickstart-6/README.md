# QUICKSTART

> Get up and running with CloudCurio Monorepo in under 5 minutes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quickstart Guide

Get up and running with CloudCurio Monorepo in under 5 minutes.

## Prerequisites

Before starting, ensure you have:

- **Python 3.10 or higher** with pip and venv
- **Node.js 18 or higher** (for MCP servers)
- **Git 2.30+**
- **Docker & Docker Compose** (optional, for observability)
- **~500MB disk space** for dependencies

Check your versions:
```bash
python --version   # Should be 3.10+
node --version     # Should be v18+
git --version      # Should be 2.30+
```

## Step 1: Clone or Extract Repository

If cloning from GitHub:
```bash
cd ~/Documents
mkdir -p cloudcurio_monorepo
cd cloudcurio_monorepo
git clone <repository-url> cloudcurio-monorepo
cd cloudcurio-monorepo
```

If using a zip distribution:
```bash
cd ~/Documents
mkdir -p cloudcurio_monorepo
cd cloudcurio_monorepo
unzip cloudcurio-monorepo-FINAL.zip -d .
cd cloudcurio-monorepo
```

## Step 2: Bootstrap the Environment

Run the automated bootstrap script:
```bash
./scripts/bootstrap.sh
```

This script will:
1. ✅ Create Python virtual environment in `.venv/`
2. ✅ Install Python dependencies from `pyproject.toml`
3. ✅ Install pre-commit hooks for code quality
4. ✅ Verify CLI tools are properly installed
5. ✅ Run initial sanity checks

**Expected output:**
```
✓ Python virtual environment created
✓ Dependencies installed
✓ Pre-commit hooks installed
✓ CLI tools verified
✓ Bootstrap complete!
```

## Step 3: Verify Installation

Run the health check to ensure everything is configured correctly:
```bash
make doctor
```

This validates:
- ✅ Python environment and dependencies
- ✅ CLI tools are in PATH
- ✅ Directory structure is intact
- ✅ Agent specifications are valid
- ✅ Registry indexes are current

Expected output: All checks should pass with ✓ marks.

## Step 4: Generate Registry Indexes

Build the agent and tool registries:
```bash
make index
```

This creates:
- `registry/agents.json` - Catalog of all available agents
- `registry/tools.json` - Catalog of all available tools
- `regi

*[truncated — see source for full prompt]*