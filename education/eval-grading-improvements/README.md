# EVAL GRADING IMPROVEMENTS

> **Type**: Tutorial (Learning-Oriented)
**Last Updated**: 2026-02-28
**Related PRs**: [#2673](https://github.com/rysweet/amplihack/pull/2673), [#2674](

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Eval Grading Improvements Tutorial

**Type**: Tutorial (Learning-Oriented)
**Last Updated**: 2026-02-28
**Related PRs**: [#2673](https://github.com/rysweet/amplihack/pull/2673), [#2674](https://github.com/rysweet/amplihack/pull/2674)

## Overview

This tutorial teaches you how to fix grader false negatives and implement advanced retrieval strategies for eval systems. These improvements increased evaluation accuracy from 96.0% to 97.8% in the amplihack eval system.

## What You'll Learn

1. How to fix grader false negatives using deterministic patterns
2. How to implement entity-linked retrieval for structured IDs
3. How to implement multi-entity retrieval for multi-hop reasoning
4. Best practices for combining deterministic and semantic grading

## Prerequisites

- Basic understanding of LLM-based evaluation systems
- Familiarity with semantic similarity grading
- Knowledge of information retrieval concepts

## Problem: Grader False Negatives

### The Issue

Consider this question and answer:

**Question**: "What is the current project budget?"
**Expected**: "$1.4M"
**Agent Answer**: "The budget increased from $1.2M to $1.4M"

The agent's answer contains the correct current value ($1.4M) but also mentions the historical value ($1.2M). A naive grader using incorrect patterns might score this as 0% because $1.2M appears in the answer and matches an "incorrect pattern" for the historical value.

### The Root Cause

The grader was checking for incorrect patterns WITHOUT first verifying that the correct answer was present:

```python
# BUGGY VERSION (from before PR #2674)
if any(pattern in answer.lower() for pattern in incorrect_patterns):
    score = 0.0  # Wrong! Penalizes even when correct answer is present
```

This caused false negatives when answers contained both historical and current information.

## Solution 1: Fix Deterministic Grading Logic

### The Fix

Only apply incorrect pattern penalties when the correct keywords are NOT present:

```python
# FIXED VER

*[truncated — see source for full prompt]*