# Permission Boundaries

> > Define what the agent can touch before it starts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Permission Boundaries

> Define what the agent can touch before it starts. Don't react to damage after the fact.

## The Problem

An agent with full access will eventually do something irreversible: delete a branch, push to main, drop a table, or send a message to a customer. These mistakes don't come from bad prompts — they come from the agent having more access than the task requires.

## The Pattern

Encode permissions as a constraint set that is evaluated **before** a tool is called, not after. Apply the minimum set of tools required for the task. Trust-gate broader access behind confirmation.

### Three Layers

```
Layer 1: Tool filtering (what tools the model can see)
Layer 2: Runtime blocking (what calls are intercepted)
Layer 3: Confirmation gates (what requires explicit approval)
```

Each layer is independent. Use all three in production workflows.

---

### Layer 1: Tool Filtering

Pass only the tools relevant to the task in the system prompt or tool list. Tools the model doesn't know about cannot be called.

```
Task: "Review this PR for security issues"
Tools: read_file, search_code, add_pr_comment
Excluded: merge_pr, push_files, delete_branch, run_bash
```

For Claude Code, use MCP server activation to control tool visibility. Servers not listed in `.mcp.json` provide no tools.

### Layer 2: Runtime Blocking

Even with a filtered list, intercept tool calls before execution. Block by name or prefix.

```python
# Block all destructive filesystem operations
SAFE_MODE = PermissionContext(
    deny_names={"delete_file", "write_file"},
    deny_prefixes={"execute_", "run_", "create_"}
)

def before_tool_call(tool_name: str, args: dict) -> bool:
    if SAFE_MODE.blocks(tool_name):
        log_denial(tool_name, args)
        return False  # blocked
    return True  # allowed
```

Log every denial. Patterns in denial logs reveal when a task needs broader permissions or when a prompt is misdirected.

### Layer 3: Confirmation Gates

Some tools are allowed but 

*[truncated — see source for full prompt]*