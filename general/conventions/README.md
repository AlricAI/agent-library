# CONVENTIONS

> This document defines the git branching strategy and conventions that all teams across the organization must follow.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Organization-Wide Git Branching Strategy

This document defines the git branching strategy and conventions that all teams across the organization must follow. These standards ensure consistency, improve collaboration, and streamline our development and deployment processes.

## Table of Contents
1. [Overview](#overview)
2. [Core Branching Model](#core-branching-model)
3. [Branch Naming Conventions](#branch-naming-conventions)
4. [Workflow Processes](#workflow-processes)
5. [Commit Standards](#commit-standards)
6. [Branch Protection Rules](#branch-protection-rules)
7. [Team-Specific Guidelines](#team-specific-guidelines)
8. [Tool Integration](#tool-integration)
9. [Migration Strategy](#migration-strategy)
10. [Quick Reference](#quick-reference)

## Overview

This branching strategy is designed to:
- Provide consistency across all teams (Software, Marketing, Product, Cyber)
- Enable clear tracking of work items
- Support continuous integration and deployment
- Facilitate collaboration between teams
- Maintain code quality and stability

## Core Branching Model

### Main Branches

```
main (or master)
    │
    ├── develop
    │     │
    │     └── feature branches
    │
    ├── release branches
    │
    └── hotfix branches
```

#### 1. **main** (Production)
- Contains production-ready code
- Protected branch - no direct commits
- All changes via pull requests
- Tagged for releases
- Deployment trigger for production

#### 2. **develop** (Integration)
- Integration branch for features
- Protected branch - no direct commits
- Base for all feature branches
- Regularly updated from main
- Deployment trigger for development environment

#### 3. **staging** (Optional)
- Pre-production testing
- Mirror of production environment
- Final validation before production
- Used for UAT and performance testing

### Supporting Branches

#### Feature Branches
- Created from: `develop`
- Merge back to: `develop`
- Naming: `feature/<team>-<ticket>-<description>`
- Lifespan: Until fea

*[truncated — see source for full prompt]*