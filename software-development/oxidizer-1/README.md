# OXIDIZER

> The Oxidizer workflow automates Python-to-Rust migration through iterative
convergence loops. It treats the Python codebase as the living specificatio

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Oxidizer Workflow

The Oxidizer workflow automates Python-to-Rust migration through iterative
convergence loops. It treats the Python codebase as the living specification
and produces a fully-tested Rust equivalent with zero-tolerance parity
validation.

## Overview

Oxidizer is a recipe-driven workflow that:

- Analyzes the Python codebase (AST, dependencies, types, public API)
- Ensures complete test coverage before any porting begins
- Scaffolds a Rust project with the correct structure
- Ports tests first, then implementation module-by-module
- Runs quality and degradation audits on every iteration
- Loops until 100% feature parity is achieved

## Quick Start

```bash
recipe-runner-rs amplifier-bundle/recipes/oxidizer-workflow.yaml \
  --set python_package_path=src/mypackage \
  --set rust_target_path=rust/mypackage \
  --set rust_repo_name=my-rust-crate \
  --set rust_repo_org=myorg
```

## Required Context Variables

| Variable              | Description                           | Example                   |
| --------------------- | ------------------------------------- | ------------------------- |
| `python_package_path` | Path to the Python package to migrate | `src/amplihack/recipes`   |
| `rust_target_path`    | Where to create the Rust project      | `rust/recipe-runner`      |
| `rust_repo_name`      | GitHub repository name for the output | `amplihack-recipe-runner` |
| `rust_repo_org`       | GitHub org or user                    | `rysweet`                 |

## Workflow Phases

### Phase 1: Analysis

Performs comprehensive analysis of the Python codebase:

- AST analysis of every module
- Dependency graph mapping
- Type inference for function signatures
- Public API surface extraction
- Migration priority ordering (leaf modules first)

### Phase 1B: Test Completeness Gate

**This gate blocks all further progress until test coverage is sufficient.**

1. Measures current Python test coverage
2. Identifies untested code paths
3. Writes missing test

*[truncated — see source for full prompt]*