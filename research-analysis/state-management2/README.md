# State Management2

> Based on the research, several significant problems arise when integrating LangGraph with FastMCP, particularly around **Command object returns**, **s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Problems When Combining LangGraph with FastMCP: Command Objects and State Management Issues

Based on the research, several significant problems arise when integrating LangGraph with FastMCP, particularly around **Command object returns**, **state management**, and **tool execution isolation**. Here are the key issues you should be aware of:

## Critical Command Object Problems

### 1. **State Updates Not Persisting from Command Returns**

Tools that return `Command` objects for state updates often fail to properly propagate state changes in LangGraph workflows. This is especially problematic with MCP tools:[1][2]

```python
@tool(return_direct=True)
async def mcp_tool_with_state_update() -> Command:
    """MCP tool that tries to update state"""
    return Command(
        update={"model_context": ["Updated data from MCP"]},
        goto="next_node"
    )
```

**Problem**: The state update occurs within the Command but doesn't persist to subsequent nodes - the original values remain unchanged.[2]

### 2. **Tool State Injection Incompatibility**

MCP tools loaded via `langchain-mcp-adapters` have limited support for LangGraph's `InjectedState` functionality:[3][4][5]

```python
# This pattern DOESN'T work reliably with MCP tools
@tool
async def mcp_tool_with_injected_state(
    query: str,
    state: Annotated[MyState, InjectedState]  # Problematic with MCP
) -> str:
    context = state.get("context", "")
    return f"MCP result with context: {context}"
```

**Issue**: MCP tools created through `load_mcp_tools()` don't properly support injected state parameters, limiting their ability to access and modify graph state.[4][3]

## Parameter Recognition and Streaming Issues

### 3. **astream_events Parameter Mangling**

When using `astream_events` with MCP tools, parameter recognition fails catastrophically:[6]

```python
# Expected: {"weight": 80, "height": 1.8}
# Actual with astream_events: {"weighight": 1.8}  # Parameters merged/corrupted
```

**Impact**: This cause

*[truncated — see source for full prompt]*