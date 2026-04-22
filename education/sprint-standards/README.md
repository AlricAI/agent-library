# SPRINT STANDARDS

> **Version**: 1.0.0
**Effective**: Sprint 6+
**Last Updated**: 2025-11-08
**Purpose**: Codify lessons learned from Sprints 0-5 and establish clear stan

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sprint Standards and Process

**Version**: 1.0.0
**Effective**: Sprint 6+
**Last Updated**: 2025-11-08
**Purpose**: Codify lessons learned from Sprints 0-5 and establish clear standards for all future sprints

---

## Table of Contents

1. [Pre-Sprint Planning](#pre-sprint-planning)
2. [Speckit Workflow (MANDATORY)](#speckit-workflow-mandatory)
3. [Sprint Execution Standards](#sprint-execution-standards)
4. [Testing Requirements](#testing-requirements)
5. [Documentation Standards](#documentation-standards)
6. [Git Workflow](#git-workflow)
7. [Quality Gates](#quality-gates)
8. [Sprint Retrospective](#sprint-retrospective)
9. [Sprint 6+ Checklist](#sprint-6-checklist)
10. [Templates and Examples](#templates-and-examples)

---

## Pre-Sprint Planning

### When to Create a New Sprint vs Extend Existing

**Create a new sprint when**:
- Previous sprint is complete and merged to main
- New feature requires distinct specification (different user stories)
- Sprint scope is substantially different from previous work
- Calendar week boundary crossed (sprints typically 1-2 weeks)

**Extend existing sprint when**:
- Adding P2/P3 features to partially-complete sprint
- Fixing bugs discovered in sprint testing
- Completing deferred tasks from sprint backlog
- Sprint duration is still within 2-week window

**Examples from Sprints 0-5**:
- ✅ Sprint 4.5 created: Schema refactoring was distinct from multi-agent work
- ✅ Sprint 5 created: Async migration was architectural change requiring new spec
- ❌ Should have extended Sprint 4: Adding AgentCard UI (actually done correctly as part of Sprint 4)

### Sprint Naming Convention

**Format**: `sprint-NN-short-name.md`

**Rules**:
- **NN**: Two-digit sprint number (00, 01, 02..., 10, 11...)
- **short-name**: 2-4 words, lowercase, hyphen-separated
- **short-name style**: Action-oriented or feature-focused
  - Good: `async-workers`, `human-loop`, `multi-agent`
  - Bad: `phase2`, `updates`, `improvements`

**Examples**:
- `sprint-00-foundati

*[truncated — see source for full prompt]*