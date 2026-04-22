# AI AGENT BEST PRACTICES

> **Research Date:** 2026-03-31  
**Purpose:** Research for ModPorter-AI v2.5 automation improvements

---

## 1. Context Management for AI Coding Agent

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Agent Software Development Best Practices

**Research Date:** 2026-03-31  
**Purpose:** Research for ModPorter-AI v2.5 automation improvements

---

## 1. Context Management for AI Coding Agents

### 1.1 CLAUDE.md / Context Files

**Best Practice:** Aggressively manage context through project-specific configuration files.

```
Key Patterns:
├── CLAUDE.md          # Project overview, architecture, conventions
├── .claude/           # Agent-specific configurations
├── skills/            # Reusable task patterns
└── memory/            # Cross-session persistent memory
```

**Key Insight:** "Context degradation is the primary failure mode for AI coding agents" - Claude Code Best Practices

**Recommendations:**
- Keep CLAUDE.md concise (<500 lines)
- Include project structure, naming conventions, coding standards
- Document forbidden patterns (e.g., no regex, no vulnerable patterns)
- Use context compression for large codebases

### 1.2 Subagent Architecture

**Best Practice:** Decompose complex tasks into small, focused sub-agents.

From Claude Code subagent documentation:

| Pattern | Use Case | Example |
|---------|----------|---------|
| **Task-specific** | One-off coding tasks | Review PR, Write tests |
| **Role-based** | Specialized expertise | Security auditor, API designer |
| **Orchestrated** | Multi-step workflows | Implement feature E2E |

**Subagent Design Principles:**
1. **Single responsibility** - One clear goal per agent
2. **Explicit inputs/outputs** - Typed interfaces between agents
3. **Token budgets** - Prevent context overflow
4. **Retry logic** - Handle failures gracefully

---

## 2. Multi-Agent Orchestration Patterns

### 2.1 Core Patterns (from Azure AI Architecture)

| Pattern | Description | Best For |
|---------|-------------|----------|
| **Sequential** | Agents execute one after another | Linear workflows (analyze → implement → test) |
| **Parallel** | Multiple agents work simultaneously | Independent tasks (lint, test, build) |
| **Sup

*[truncated — see source for full prompt]*