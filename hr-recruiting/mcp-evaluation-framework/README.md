# MCP EVALUATION FRAMEWORK

> ## Purpose

Generic, reusable framework for evaluating ANY MCP server integration with amplihack. Measures real value through controlled comparisons o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP Evaluation Framework

## Purpose

Generic, reusable framework for evaluating ANY MCP server integration with amplihack. Measures real value through controlled comparisons of baseline vs tool-enhanced coding workflows.

## Architecture

### Core Components

```
┌─────────────────────────────────────────────────────┐
│         Evaluation Framework (Generic)              │
│  ┌────────────┐  ┌──────────┐  ┌────────────────┐ │
│  │  Scenario  │→ │ Executor │→ │ Metrics        │ │
│  │  Runner    │  │          │  │ Collector      │ │
│  └────────────┘  └──────────┘  └────────────────┘ │
│         ↓              ↓               ↓            │
└─────────────────────────────────────────────────────┘
         ↓              ↓               ↓
┌─────────────────────────────────────────────────────┐
│         Tool Adapters (Tool-Specific)               │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────┐ │
│  │  Serena  │  │ Copilot  │  │  Future Tool    │ │
│  │ Adapter  │  │ Adapter  │  │  Adapter        │ │
│  └──────────┘  └──────────┘  └──────────────────┘ │
└─────────────────────────────────────────────────────┘
```

### Design Principles

1. **Brick Design**: Framework is regeneratable, each component has ONE responsibility
2. **Ruthless Simplicity**: Core framework is <500 lines, complexity in adapters
3. **Measurement-Driven**: Real execution data, not synthetic benchmarks
4. **Zero Future-Proofing**: Design for Serena NOW, extend naturally later

## Test Scenario Design

### Generic Test Categories

Three categories that reveal MCP tool value WITHOUT assuming specific capabilities:

#### Test Category 1: Cross-File Code Navigation

**Generic Skill**: Finding code across multiple files
**Baseline Approach**: grep, glob, sequential file reading
**MCP Enhancement**: Tool-specific navigation features

**Example Test**: "Find all implementations of interface `Handler` across codebase"

**Evaluation Points**:

- How many files examined?
- How many false positives?
- 

*[truncated — see source for full prompt]*