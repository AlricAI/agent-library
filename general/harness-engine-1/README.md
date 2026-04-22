# Harness Engine

> > Full-stack agent execution harness with Langfuse observability, state management,
> sandboxed execution, context compression, validation loops, and 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Harness Engine

> Full-stack agent execution harness with Langfuse observability, state management,
> sandboxed execution, context compression, validation loops, and multi-agent fan-out.

## 8 Pillars

### 1. Langfuse Observability (AI Automators pattern)
- Session-level trace per conversation (created at SessionStart hook)
- Automatic span per tool call (PreToolUse opens, PostToolUse closes)
- Generation tracking for LLM API calls (`langfuse_model_proxy.py`)
- Scoring: cache_hit, retrieval_quality, compression_ratio, tool_error
- Cost/token tracking, latency percentiles
- Dashboard: `langfuse_dashboard.py overview|compare|traces|errors|slow`

### 2. State Management (inside the harness)
- File-based state protocol: `.tmp/harness_state.json`
- Session state: trace_id, span stack, open tasks, current phase
- State machine: `init → planning → executing → validating → complete`
- Rollback on failure, orphan cleanup at session end

### 3. Human-in-the-Loop + Fan-Out via Pulsar
- Qdrant shared memory: pull/push for cross-agent context
- Pulsar message bus (`docker-compose.pulsar.yml`) for fan-out
- Any agent (Gemini, Cursor, Copilot) picks up work, executes, pushes results
- Human approval gates via Telegram channel or CLI

### 4. Orchestrator on Powerful Models
- Planning + orchestration → Opus (expensive, accurate)
- Execution/sub-tasks → Haiku/Sonnet (cheap, fast)
- `langfuse_model_proxy.py` records every generation with model/tokens/cost
- Dashboard shows cost breakdown by model

### 5. Sandboxed Execution
- Commands run in Docker containers (`fastapi_tool_bridge.py` pattern)
- Harness validates outputs before state changes
- Destructive command blocking, timeout enforcement
- Subprocess isolation for untrusted code

### 6. Context Management + Compression
- Sub-agents get minimal relevant context (not full conversation)
- Qdrant retrieves relevant memory chunks before delegation
- Summary generation (cheap model) before sending to sub-agent
- Progressive dis

*[truncated — see source for full prompt]*