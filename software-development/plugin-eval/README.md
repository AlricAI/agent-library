# Plugin Eval

> PluginEval is a three-layer quality evaluation framework for Claude Code plugins and skills.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PluginEval: Quality Evaluation Framework

PluginEval is a three-layer quality evaluation framework for Claude Code plugins and skills. It combines deterministic static analysis, LLM-based semantic judging, and Monte Carlo simulation to produce calibrated quality scores with confidence intervals.

## Overview

PluginEval answers the question: **"How good is this plugin or skill?"** It evaluates across 10 quality dimensions, detects anti-patterns, assigns letter grades, and awards quality badges (Bronze through Platinum).

### Architecture

```
┌─────────────────────────────────────────────────┐
│                   CLI / Commands                │
│       score · certify · compare · init          │
├─────────────────────────────────────────────────┤
│                   Eval Engine                   │
│         Composite scoring, layer blending       │
├────────────┬────────────────┬───────────────────┤
│  Layer 1   │    Layer 2     │     Layer 3       │
│  Static    │   LLM Judge    │   Monte Carlo     │
│  Analysis  │   (Semantic)   │   (Statistical)   │
│  <2s, free │  ~30s, 4 calls │  ~2min, 50 calls  │
├────────────┴────────────────┴───────────────────┤
│                  Parser Layer                   │
│       SKILL.md, agents/*.md, plugin.json        │
├─────────────────────────────────────────────────┤
│              Statistical Methods                │
│    Wilson CI · Bootstrap CI · Clopper-Pearson    │
│    Cohen's κ · Coefficient of Variation         │
├─────────────────────────────────────────────────┤
│              Corpus & Elo Ranking               │
│    Gold standard index · Pairwise comparison    │
└─────────────────────────────────────────────────┘
```

## Installation & Setup

PluginEval lives in `plugins/plugin-eval/` and uses [uv](https://docs.astral.sh/uv/) for dependency management.

```bash
cd plugins/plugin-eval

# Install core dependencies (static analysis only)
uv sync

# Install with LLM support (Layers 2 & 3)
uv sync --extra llm

# Inst

*[truncated — see source for full prompt]*