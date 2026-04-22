# PLANNING SUMMARY

> **Date**: 2025-11-08  
**Status**: Planning Complete ✅ - Ready for Implementation

---

## Overview

Complete plan created for transitioning from Mock

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Real Agents Planning Summary 📋

**Date**: 2025-11-08  
**Status**: Planning Complete ✅ - Ready for Implementation

---

## Overview

Complete plan created for transitioning from MockAgent test agents to **real LLM-powered agents** using litellm. The foundation (BaseAgent, ReaderAgent, tools) already exists - we just need to refactor to event-based architecture and add 2 more agent types.

---

## Key Design Decisions ⭐

### 1. Event-Based Architecture (Generator Pattern)

**Decision**: All agents yield events, AgentRunner consumes them

**Why**: 
- ✅ Clean separation (agents produce, runner logs)
- ✅ No monkey-patching needed
- ✅ Easy to test
- ✅ Following proven mockecy pattern

```python
# Agent yields
yield {'type': 'text_token', 'content': 'Hello'}
yield {'type': 'tool_call', 'tool': 'advance', 'args': {...}}

# AgentRunner logs
for event in agent.run_forever(...):
    log_event(event)
```

### 2. Line-at-a-Time Buffering

**Decision**: Flush on newlines + tool calls (not per-token)

**Why**:
- With 3-10 agents running, per-token logging would overwhelm system
- Line-by-line is responsive but not overwhelming
- Still feels real-time for frontend

### 3. 300k Character Context Limit

**Decision**: Hard stop at 300k, raise exception

**Why**:
- Prevent runaway API costs
- Force us to implement summarization later
- Check happens before LLM call

### 4. Tool Errors as Results

**Decision**: Tool exceptions become `{'error': '...', 'success': False}` results

**Why**:
- Agent can see and respond to errors
- More robust than crashing
- Matches real-world tool behavior

### 5. Thinking Tokens Separate from Text

**Decision**: Yield `thinking_token` events separately

**Why**:
- Different UI presentation
- Can be logged separately
- Matches Claude's extended thinking feature

### 6. File-Based Streaming (For Now)

**Decision**: `Agent → Log File → LogManager → SSE → UI`

**Why**:
- Simpler (unify log and frontend streams)
- Can add dual-feed later if needed
- File w

*[truncated — see source for full prompt]*