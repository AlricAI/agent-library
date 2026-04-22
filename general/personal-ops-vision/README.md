# PERSONAL OPS VISION

> ## Project Vision

Transform OOS from infrastructure foundation into a **Personal Operational Intelligence System** that:
- Mines your GitHub reposito

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Personal Operational Intelligence System - Vision Document

## Project Vision

Transform OOS from infrastructure foundation into a **Personal Operational Intelligence System** that:
- Mines your GitHub repositories for scattered ideas, themes, and concepts
- Converts those insights into actionable slash commands within Claude Code
- Creates intelligent command orchestration (like `/check-all` running commands 1,4,5,11 in logical order)
- Provides a single source of truth for your development patterns, accessible via `/helpme`

## Core Components

### 1. Repository Mining Engine
- **Target Repos**: Atlas, ralex, agent-os, atlas-code, atlas-coder
- **Source Material**: Documentation, README files, issues, commit messages (NOT code comments)
- **Output**: Extracted ideas, themes, and concepts with automatic categorization

### 2. Idea → Command Generator
- **Input**: Scattered thoughts and themes from repository mining
- **Process**: Transform insights into consistent `/command-name` format
- **Examples**:
  - Theme: "Always validate environment setup" → `/env-validate`
  - Idea: "Document decision rationale" → `/decision-log`
  - Pattern: "Health check everything" → `/health-check-all`

### 3. Command Orchestration Engine
- **Capability**: Chain commands intelligently based on dependencies and context
- **Examples**:
  - `/check-all` - Runs commands 1,4,5,11,29,19,5 in logical order
  - `/pre-deploy` - Runs environment, security, health checks in sequence
  - `/project-setup` - Runs initialization commands in proper dependency order
  - `/debug-flow` - Runs diagnostic commands in troubleshooting sequence
- **Features**: Dependency management, conditional execution, failure handling, context awareness

### 4. Claude Code Integration Layer
- **Interface**: Native slash command integration within Claude Code
- **User Experience**: No context switching, natural language interaction
- **Help System**: `/helpme` command showing all available commands with consistent n

*[truncated — see source for full prompt]*