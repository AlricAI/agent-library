---
name: Installation
description: This guide covers the installation of ClawArena, the four supported agent frameworks, and MetaClaw.
model: claude-sonnet-4-5
---
# Installation Guide

This guide covers the installation of ClawArena, the four supported agent frameworks, and MetaClaw.

---

## Quick Setup (Recommended)

The setup script installs ClawArena and all supported framework CLIs in one command:

```bash
bash scripts/setup.sh
```

It will:
1. Install ClawArena in editable mode with dev dependencies
2. Install Python SDKs (claude-agent-sdk, nanobot-ai)
3. Install Claude Code CLI via npm (requires Node.js)
4. Install PicoClaw via Go (auto-installs Go ≥ 1.25 if needed)
5. Verify all installations and report status

After setup, verify:

```bash
clawarena --help
```

If you need more control, follow the manual steps below.

---

## Manual Installation

### 1. ClawArena

**Requirements**: Python ≥ 3.10, pip

```bash
# Basic install
pip install -e .

# With development tools (pytest, etc.)
pip install -e ".[dev]"
```

ClawArena's core depends only on `pandas` and `scipy`. Framework-specific SDKs are optional:

```bash
pip install -e ".[claude-code]"    # Claude Code Python SDK
pip install -e ".[nanobot]"        # Nanobot Python SDK
pip install -e ".[all]"            # All optional dependencies
```

### 2. Framework CLIs

Install only the frameworks you plan to evaluate.

#### OpenClaw

[OpenClaw](https://openclaw.ai) is a Node.js-based CLI agent.

```bash
# Requires Node.js and npm
npm install -g @anthropic-ai/claude-code   # OpenClaw depends on this
```

Refer to the [OpenClaw documentation](https://openclaw.ai) for full setup instructions including API key configuration.

#### Claude Code

[Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code) is Anthropic's agentic coding tool.

```bash
# Requires Node.js and npm
npm install -g @anthropic-ai/claude-code
```

Authenticate:

```bash
claude login
```

The ClawArena engine also requires the Python SDK:

```bash
pip install claude-agent-sdk
```

#### PicoClaw

[PicoClaw](https://github.com/sipeed/picoclaw) is a Go-based CLI agent.

```bash
# Requires Go ≥ 1.25
go install github.com/sipeed/picoclaw/cmd/picoclaw@latest
```

If Go is not installed, the setup script auto-installs it to `~/.local/go-sdk`. Make sure the binary directory is in your PATH:

```bash
export PATH="$HOME/go/bin:$HOME/.local/bin:$PATH"
```

#### Nanobot

[Nanobot](https://github.com/qwibitai/nanoclaw) is a Python-native CLI agent.

```bash
pip install nanobot-ai
```

---

## 3. MetaClaw (Optional)

[MetaClaw](https://github.com/aiming-lab/MetaClaw) is an optional proxy layer that enhances agents with memory, skills, and RL during evaluation. ClawArena supports MetaClaw with **OpenClaw** and **Nanobot**.

### Install

```bash
git clone https://github.com/aiming-lab/MetaClaw.git
cd MetaClaw
pip install -e .
```

### Configure

```bash
metaclaw setup
```

The interactive wizard will ask for your LLM provider, API key, and preferred agent.

### Use with ClawArena

Add the `metaclaw` field to your `tests.json`:

```json
{
  "metaclaw": {
    "enabled": true,
    "managed": true,
    "config_path": "metaclaw/memory.yaml"
  }
}
```

Then run as usual — ClawArena manages the MetaClaw proxy lifecycle automatically:

```bash
clawarena run --data data/clawarena/tests.json --frameworks openclaw --out output/
```

See [MetaClaw Guide](metaclaw-guide.md) for managed/unmanaged modes and trigger configuration.

---

## Environment Variables

ClawArena uses `CLAWARENA_*` environment variables for LLM provider configuration:

| Variable | Description |
|----------|-------------|
| `CLAWARENA_PROVIDER` | LLM provider type (openai, anthropic, claude, etc.) |
| `CLAWARENA_MODEL_ID` | Model name (e.g., `gpt-4o`, `claude-opus-4-6`) |
| `CLAWARENA_API_BASE` | API endpoint URL |
| `CLAWARENA_API_KEY` | Authentication key |

These can also be set via CLI flags (`--provider`, `--model-id`, `--api-base`, `--api-key`) or in `tests.json`. See [Provider Guide](provider-usage-guide.md) for the full priority chain.