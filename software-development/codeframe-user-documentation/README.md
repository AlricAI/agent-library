# CODEFRAME USER DOCUMENTATION

> ## Overview

CodeFRAME is an autonomous AI development system that enables multiple specialized agents to collaborate and build software features end-

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME User Documentation

## Overview

CodeFRAME is an autonomous AI development system that enables multiple specialized agents to collaborate and build software features end-to-end. It's designed to work autonomously while providing human-in-the-loop capabilities when agents encounter blockers or need decisions.

## Key Features

### 1. Multi-Agent System
- **Lead Agent**: Orchestrates the entire development process, handles discovery, and coordinates other agents
- **Backend Worker Agent**: Specializes in Python/FastAPI backend development
- **Frontend Worker Agent**: Handles React/TypeScript frontend development  
- **Test Worker Agent**: Creates and runs tests, analyzes test results
- **Review Worker Agent**: Performs code reviews and quality checks

### 2. Autonomous Development Workflow
1. **Discovery Phase**: Lead agent asks intelligent questions to understand requirements
2. **Planning Phase**: System generates Product Requirements Document (PRD) and decomposes into executable tasks
3. **Execution Phase**: Worker agents autonomously implement tasks, run tests, and fix issues
4. **Review Phase**: Code review agents check quality and enforce standards
5. **Deployment Phase**: Completed features are automatically committed and merged

### 3. Quality Enforcement
- **Automated Testing**: Integrated pytest and other test frameworks
- **Self-Correction**: Agents automatically fix failing tests (up to 3 attempts)
- **Quality Gates**: Pre-completion checks for tests, coverage, and code quality
- **Code Review**: Automated security scanning and complexity analysis
- **Lint Enforcement**: Multi-language linting with trend tracking

### 4. Context Management
- **Tiered Memory System**: HOT/WARM/COLD memory tiers reduce token usage by 30-50%
- **Flash Save Mechanism**: Automatic context preservation before token limits are reached
- **Session Lifecycle**: Auto-save and restore work context across CLI restarts
- **Checkpoint & Recovery**: Git + database snapshots e

*[truncated — see source for full prompt]*