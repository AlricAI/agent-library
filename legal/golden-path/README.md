# GOLDEN PATH

> This document is the contract for CodeFRAME v2 development.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME v2 — Golden Path Contract (CLI-first)

This document is the contract for CodeFRAME v2 development.

**Rule 0 (the only rule that matters):**
> If a change does not directly support the Golden Path flow below, do not implement it.

This applies to both humans and agentic coding assistants.

---

## Goals

### What "done" looks like (Enhanced MVP definition)
CodeFRAME can run a complete end-to-end AI-driven development workflow **from the CLI** on a target repo:

1) **Initialize workspace with project discovery**
   - Analyze codebase and detect tech stack
   - Configure environment and tooling automatically
   - Create durable state storage

2) **AI-driven PRD generation and refinement**
   - Interactive AI session gathers project requirements
   - AI asks follow-up questions about scope, users, constraints
   - Generates comprehensive PRD + technical specs + user stories
   - Iterative refinement based on user feedback

3) **Intelligent task generation with dependency analysis**
   - Decompose PRD into actionable tasks with dependencies
   - Prioritize tasks and group by functionality
   - Generate implementation strategies per task

4) **Batch task execution with orchestration**
   - Execute multiple tasks in sequence or parallel
   - Handle inter-task dependencies automatically
   - Main agent coordinates entire batch workflow
   - Real-time progress monitoring and event streaming

5) **Human-in-the-loop blocker resolution**
   - Interactive blocker handling with contextual AI suggestions
   - Resume execution after blocker resolution
   - Learning from blocker patterns

6) **Integrated Git workflow and PR management**
   - Automatic branch creation per task/batch
   - AI-generated commit messages and PR descriptions
   - Automated verification gate execution
   - PR creation, review, and merging workflows

7) **Comprehensive checkpointing and state management**
   - Snapshots of workspace state with git refs
   - Resume interrupted workflows from chec

*[truncated — see source for full prompt]*