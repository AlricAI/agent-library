# Installation

> This guide covers the installation of ClawArena, the four supported agent frameworks, and MetaClaw.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
# Requires Go

*[truncated — see source for full prompt]*