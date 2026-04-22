# PreCommitHooks

> ## Overview

Automated code quality enforcement system using the pre-commit framework to ensure consistent code standards across Python, JavaScript/Ty

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pre-Commit Hooks Specification

## Overview

Automated code quality enforcement system using the pre-commit framework to ensure consistent code standards across Python, JavaScript/TypeScript, and documentation files.

## Architecture

### Core Components

1. **Pre-commit Framework**: Python-based git hooks manager
2. **Language-specific Tools**: Isolated virtual environments per tool
3. **Configuration Files**: YAML and JSON configs for tools
4. **Custom Hooks**: Project-specific philosophy compliance

### Hook Execution Flow

```
git commit → pre-commit → parallel hook execution → pass/fail → commit/abort
```

## Hooks Configuration

### Performance Tiers

**Tier 1: Ultra-Fast (<50ms)**

- trailing-whitespace
- end-of-file-fixer
- check-merge-conflict
- detect-private-key
- mixed-line-ending

**Tier 2: Fast (<200ms)**

- check-yaml
- check-json
- ruff (Python format/lint)

**Tier 3: Moderate (<500ms)**

- prettier (JS/TS/MD formatting)
- markdownlint
- pyright (type checking)

**Tier 4: Variable (on-demand)**

- pytest-changed (only changed tests)
- philosophy-check (custom)

### Language Support

#### Python

- **Formatting**: ruff format
- **Linting**: ruff (E, W, F, I, B, C4, UP, ARG, SIM rules)
- **Type Checking**: pyright (standard mode)
- **Testing**: pytest (changed files only)

#### JavaScript/TypeScript

- **Formatting**: prettier
- **Linting**: eslint (optional, not configured)

#### Markdown

- **Formatting**: prettier
- **Linting**: markdownlint

#### JSON/YAML

- **Formatting**: prettier
- **Validation**: check-json, check-yaml

## Installation

### Quick Start

```bash
# Run the installation script
./scripts/install-hooks.sh
```

### Manual Installation

```bash
# Install pre-commit
pip3 install --user pre-commit

# Install hooks in repository
pre-commit install

# Update hooks to latest versions
pre-commit autoupdate

# Create secrets baseline
detect-secrets scan > .secrets.baseline
```

## Usage

### Normal Workflow

```bash
# Stage changes
git ad

*[truncated — see source for full prompt]*