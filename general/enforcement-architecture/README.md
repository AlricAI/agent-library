# ENFORCEMENT ARCHITECTURE

> ## Executive Summary

Sprint 8 implemented a **dual-layer quality enforcement system** that prevents common AI agent failure modes. The architecture c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Quality Enforcement - Dual-Layer Architecture

## Executive Summary

Sprint 8 implemented a **dual-layer quality enforcement system** that prevents common AI agent failure modes. The architecture correctly distinguishes between:

1. **Layer 1 (Python-specific)**: Tools for enforcing quality on codeframe's own Python development
2. **Layer 2 (Language-agnostic)**: Framework for enforcing quality on agents working on ANY language/project

This document explains the architecture, rationale, and usage of both layers.

---

## The Problem We Solved

### Original Issue
Initial implementation was Python/pytest-specific, but codeframe agents work on projects in multiple languages (Python, JavaScript, Go, Rust, Java, Ruby, C#, etc.).

### Architectural Insight
Quality enforcement serves **two distinct purposes**:

1. **Codeframe Development**: Enforce quality on codeframe's own Python codebase
2. **Agent Enforcement**: Enforce quality on whatever language/framework the agent is working on

**Wrong Approach**: One-size-fits-all Python-specific tools
**Right Approach**: Dual-layer architecture with language-agnostic agent enforcement

---

## Layer 1: Python-Specific Enforcement (Codeframe Development)

**Purpose**: Enforce quality standards on codeframe's own Python development

**Location**: `scripts/`, `.pre-commit-config.yaml`, `.claude/rules.md`

### Components

#### 1. Pre-commit Hooks (`.pre-commit-config.yaml`)
```yaml
- Black formatter
- Ruff linter
- pytest test runner (only on .py files)
- Coverage enforcement (85% minimum)
- Skip detector hook
```

#### 2. Verification Script (`scripts/verify-ai-claims.sh`)
```bash
#!/bin/bash
# 3-step verification for Python projects
# 1. Run pytest
# 2. Check coverage ≥85%
# 3. Detect skip decorator abuse
```

#### 3. Skip Detector (`scripts/detect-skip-abuse.py`)
```python
# AST-based Python skip detection
# Finds: @skip, @skipif, @pytest.mark.skip, etc.
# Exit code 1 if violations found
```

#### 4. Quality Ratchet (`scrip

*[truncated — see source for full prompt]*