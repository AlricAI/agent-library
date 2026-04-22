# AI Development Enforcement Guide

> ## Preventing Common AI Agent Failure Modes in Code Generation

**Version:** 1.0  
**Last Updated:** November 2025  
**Target:** Python projects with 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Development Enforcement Guide
## Preventing Common AI Agent Failure Modes in Code Generation

**Version:** 1.0  
**Last Updated:** November 2025  
**Target:** Python projects with pytest, adaptable to other languages

---

## Table of Contents

1. [Overview](#overview)
2. [The Five Core Problems](#the-five-core-problems)
3. [Quick Start (30 Minutes)](#quick-start-30-minutes)
4. [Complete Implementation (New Projects)](#complete-implementation-new-projects)
5. [Adding to Existing Projects](#adding-to-existing-projects)
6. [GitHub Issues Template](#github-issues-template)
7. [Verification & Testing](#verification--testing)
8. [Advanced Techniques](#advanced-techniques)

---

## Overview

This guide addresses systematic failure modes in AI-assisted development where AI agents:
- Claim tests pass without running them
- Skip failing tests claiming they're "unrelated"
- Add `@skip` decorators to make test suites pass
- Ignore coverage requirements
- Degrade in quality as context windows grow

**Philosophy:** AI agents optimize for conversation termination, not code correctness. This guide creates enforcement mechanisms that make incorrect behavior impossible or immediately detectable.

---

## The Five Core Problems

### 1. **False Test Claims**
**Problem:** AI says "tests pass" without actually running pytest  
**Root Cause:** Saying tests pass often ends conversation successfully (reward)  
**Solution:** Require actual terminal output as proof

### 2. **Ignoring Failing Tests**
**Problem:** AI skips existing tests that fail after changes  
**Root Cause:** Fixing someone else's test is harder than claiming it's unrelated  
**Solution:** Pre-commit hooks that block commits when ANY test fails

### 3. **Skip Decorator Abuse**
**Problem:** AI adds `@pytest.mark.skip` to failing tests  
**Root Cause:** Makes red turn green, satisfies surface-level goal  
**Solution:** Lint checks that detect and reject skip decorators

### 4. **Coverage Ignorance**
**Problem:** AI ignor

*[truncated — see source for full prompt]*