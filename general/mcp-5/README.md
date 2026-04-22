# MCP

> Comprehensive guide to using and extending the MCP tools infrastructure in AgentLab.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP (Model Context Protocol) Tools

Comprehensive guide to using and extending the MCP tools infrastructure in AgentLab.

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Using Existing Tools](#using-existing-tools)
- [Creating Custom Tools](#creating-custom-tools)
- [Tool Input/Output Schemas](#tool-inputoutput-schemas)
- [Error Handling](#error-handling)
- [Testing Tools](#testing-tools)
- [Registry Management](#registry-management)
- [LangChain Integration](#langchain-integration)
- [API Endpoints](#api-endpoints)

---

## Overview

MCP (Model Context Protocol) tools provide a standardized way for LLMs to interact with external functionality. Tools are:

- **Discoverable**: Tools expose their capabilities through structured schemas
- **Validated**: Inputs and outputs are validated using Pydantic models
- **Async-first**: All tools use async/await for optimal performance
- **LangChain-compatible**: Tools can be converted to LangChain format
- **Integrated with Chat**: Autonomous tool execution with memory persistence

### Built-in Tools

- **`get_current_datetime`**: Returns current date/time with format and timezone support

### Integration with Chat System

Tools are integrated with the chat system through a ReAct-style agent pattern:

1. **Autonomous Execution**: The LLM decides when to call tools based on the user's query
2. **Memory Persistence**: Tool calls and results are stored in conversation history
3. **Context Integration**: Tool results are included in the context builder for subsequent turns
4. **Iterative Reasoning**: The agent can call multiple tools sequentially until reaching a final answer

**Data Models** (defined in `src/agentlab/models/__init__.py`):

```python
@dataclass
class ToolCall:
    """Represents a tool call made by the LLM."""
    tool_name: str
    tool_args: dict[str, Any]
    call_id: str
    timestamp: datetime | None = None

@dataclass
class ToolResult:
    """Result from executing a tool call.

*[truncated — see source for full prompt]*