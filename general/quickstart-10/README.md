# QUICKSTART

> Get your project built with AI agents in minutes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME CLI Quickstart Guide

Get your project built with AI agents in minutes.

## Prerequisites

1. **Python 3.11+** with `uv` package manager
2. **LLM Provider API Key** — Anthropic is the default:
   ```bash
   export ANTHROPIC_API_KEY=sk-ant-...
   ```
   To use OpenAI-compatible providers (OpenAI, Ollama, vLLM, or any compatible endpoint):
   ```bash
   export CODEFRAME_LLM_PROVIDER=openai      # or: ollama, vllm, compatible
   export CODEFRAME_LLM_MODEL=gpt-4o         # model name for the chosen provider
   export OPENAI_API_KEY=sk-...              # required for openai; not needed for local providers
   export OPENAI_BASE_URL=http://localhost:11434/v1  # for local providers (ollama, vllm)
   ```

## The Happy Path

### Step 1: Initialize Your Workspace

Navigate to your project directory and initialize CodeFRAME with tech stack detection:

```bash
cd ~/projects/my-project
codeframe init . --detect
```

This scans your project files (pyproject.toml, package.json, Cargo.toml, go.mod) and describes your tech stack.

**Output:**
```
Workspace initialized
  Path: /home/user/projects/my-project
  ID: abc123...
  State: .codeframe/
  Tech Stack: Python with uv, pytest, ruff for linting
```

**Alternative: Explicit Tech Stack**
```bash
# Describe your stack directly
codeframe init . --tech-stack "Rust project using cargo"
codeframe init . --tech-stack "TypeScript monorepo with pnpm, Next.js, jest"

# Or use interactive mode
codeframe init . --tech-stack-interactive
```

**Why this matters:** The agent uses your tech stack description to choose appropriate commands and patterns. This works with any technology — Python, TypeScript, Rust, Go, Java, or mixed monorepos.

### Step 2: Add Your PRD

Create a markdown file describing what you want to build (e.g., `requirements.md`):

```markdown
# My Awesome App

Build a REST API for todo list management.

## Features
- Create, read, update, delete todos
- Filter by status (pending/completed)
- Priority levels (high, med

*[truncated — see source for full prompt]*