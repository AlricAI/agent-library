# AGENT SYSTEM REFERENCE

> Detailed reference for CodeFRAME's agent system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent System Reference

Detailed reference for CodeFRAME's agent system. Loaded on-demand — not required for every task.

---

## Component Table

| Component | File | Purpose |
|-----------|------|---------|
| **ReactAgent** | `core/react_agent.py` | Default engine: observe-think-act loop with tool use |
| **Tools** | `core/tools.py` | 7 agent tools: read/edit/create file, run command/tests, search, list |
| **Editor** | `core/editor.py` | Search-replace editor with 4-level fuzzy matching |
| **Stall Detector** | `core/stall_detector.py` | Synchronous stall check + StallAction enum + StallDetectedError |
| **Stall Monitor** | `core/stall_monitor.py` | Thread-based watchdog with callback (integrated into ReactAgent) |
| LLM Adapter | `adapters/llm/base.py` | Protocol, ModelSelector, Purpose enum |
| Anthropic Provider | `adapters/llm/anthropic.py` | Claude integration with streaming |
| Mock Provider | `adapters/llm/mock.py` | Testing with call tracking |
| Context Loader | `core/context.py` | Codebase scanning, relevance scoring |
| Planner | `core/planner.py` | Task → ImplementationPlan via LLM (plan engine) |
| Executor | `core/executor.py` | File ops, shell commands, rollback (plan engine) |
| Agent (legacy) | `core/agent.py` | Plan-based orchestration (--engine plan) |
| Runtime | `core/runtime.py` | Run lifecycle, engine selection, agent invocation |
| Conductor | `core/conductor.py` | Batch orchestration, worker pool |
| Dependency Graph | `core/dependency_graph.py` | DAG operations, topological sort |
| Dependency Analyzer | `core/dependency_analyzer.py` | LLM-based dependency inference |
| Environment Validator | `core/environment.py` | Tool detection and validation |
| Installer | `core/installer.py` | Cross-platform tool installation |
| Diagnostics | `core/diagnostics.py` | Failed task analysis |
| Diagnostic Agent | `core/diagnostic_agent.py` | AI-powered task diagnosis |
| Credentials | `core/credentials.py` | API key and credential management |
| Ev

*[truncated — see source for full prompt]*