# Overview

> LangGraph provides both low-level primitives and high-level prebuilt components for building agent-based applications.

## Model
- **Default:** `claude-sonnet-4-5`

## Tags
`agent`

## System Prompt
# Agent development using prebuilt components

LangGraph provides both low-level primitives and high-level prebuilt components for building agent-based applications. This section focuses on the prebuilt, ready-to-use components designed to help you construct agentic systems quickly and reliably—without the need to implement orchestration, memory, or human feedback handling from scratch.

## What is an agent?

An _agent_ consists of three components: a **large language model (LLM)**, a set of **tools** it can use, and a **prompt** that provides instructions.

The LLM operates in a loop. In each iteration, it selects a tool to invoke, provides input, receives the result (an observation), and uses that observation to inform the next action. The loop continues until a stopping condition is met — typically when the agent has gathered enough information to respond to the user.

<figure markdown="1">
![image](./assets/agent.png){: style="max-height:400px"}
<figcaption>Agent loop: the LLM selects tools and uses their outputs to fulfill a user request.</figcaption>
</figure>

## Key features

LangGraph includes several capabilities essential for building robust, production-ready agentic systems:

- [**Memory integration**](../how-tos/memory/add-memory.md): Native support for _short-term_ (session-based) and _long-term_ (persistent across sessions) memory, enabling stateful behaviors in chatbots and assistants.
- [**Human-in-the-loop control**](../concepts/human_in_the_loop.md): Execution can pause _indefinitely_ to await human feedback—unlike websocket-based solutions limited to real-time interaction. This enables asynchronous approval, correction, or intervention at any point in the workflow.
- [**Streaming support**](../how-tos/streaming.md): Real-time streaming of agent state, model tokens, tool outputs, or combined streams.
- [**Deployment tooling**](../tutorials/langgraph-platform/local-server.md): Includes infrastructure-free deployment tools. [**LangGraph Platform**](

*[truncated — see source for full prompt]*