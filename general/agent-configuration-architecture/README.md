# AGENT CONFIGURATION ARCHITECTURE

> **Date**: 2025-10-19
**Status**: Design proposal for complete integration

---

## Current State vs. Complete Vision

### ✅ What We Have Now (from ref

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Configuration & Assignment Architecture

**Date**: 2025-10-19
**Status**: Design proposal for complete integration

---

## Current State vs. Complete Vision

### ✅ What We Have Now (from refactor)

1. **AgentFactory** - Creates agents from YAML definitions
2. **AgentDefinitionLoader** - Loads and validates YAML files
3. **8 Built-in Agent Definitions** - Backend, frontend, test, etc.
4. **YAML Schema** - Includes `capabilities` field for each agent

### ❌ What's Missing (needs implementation)

1. **Project-level agent definitions** - User customization
2. **Lead Agent integration** - Discovery and registry
3. **Task capability analysis** - Extract requirements from tasks
4. **Agent assignment algorithm** - Match tasks to best agent
5. **Database schema update** - Store required capabilities on tasks

**Estimated effort to complete**: 8-10 hours

---

## Three-Tier Configuration Architecture

### Tier 1: System-Level (Admin/Developer)

**Location**: `codeframe/agents/definitions/`

**Who manages**: CodeFRAME developers, system administrators

**Purpose**: Provide battle-tested, default agent definitions

**Examples**:
```
codeframe/agents/definitions/
├── backend-worker.yaml        # General backend dev
├── backend-architect.yaml     # API design specialist
├── frontend-specialist.yaml   # UI development
├── test-engineer.yaml         # Test automation
└── code-reviewer.yaml         # Code quality
```

**Characteristics**:
- Shipped with CodeFRAME installation
- High-quality, well-tested prompts
- Updated via CodeFRAME releases
- Cannot be modified by project users
- Serve as templates for customization

---

### Tier 2: Project-Level (User/Project Owner)

**Location**: `.codeframe/agents/definitions/`

**Who manages**: Project developers, project admins

**Purpose**: Customize agents for project-specific needs

**Examples**:
```
my-project/
└── .codeframe/
    └── agents/
        └── definitions/
            ├── backend-worker.yaml      # Override system de

*[truncated — see source for full prompt]*