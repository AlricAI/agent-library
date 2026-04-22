# Context

> **Context engineering** is the practice of building dynamic systems that provide the right information and tools, in the right format, so that an AI application can accomplish a task.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Context

**Context engineering** is the practice of building dynamic systems that provide the right information and tools, in the right format, so that an AI application can accomplish a task. Context can be characterized along two key dimensions:

1. By **mutability**:
    - **Static context**: Immutable data that doesn't change during execution (e.g., user metadata, database connections, tools)
    - **Dynamic context**: Mutable data that evolves as the application runs (e.g., conversation history, intermediate results, tool call observations)
2. By **lifetime**:
    - **Runtime context**: Data scoped to a single run or invocation
    - **Cross-conversation context**: Data that persists across multiple conversations or sessions

!!! tip "Runtime context vs LLM context"

    Runtime context refers to local context: data and dependencies your code needs to run. It does **not** refer to:

    * The LLM context, which is the data passed into the LLM's prompt.
    * The "context window", which is the maximum number of tokens that can be passed to the LLM.

    Runtime context can be used to optimize the LLM context. For example, you can use user metadata
    in the runtime context to fetch user preferences and feed them into the context window.

LangGraph provides three ways to manage context, which combines the mutability and lifetime dimensions:

:::python

| Context type                                                                                | Description                                            | Mutability | Lifetime           | Access method                           |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------ | ---------- | ------------------ | --------------------------------------- |
| [**Static runtime context**](#static-runtime-context)                                       | User metadata, tools, db connections passed at startup | Static  

*[truncated — see source for full prompt]*