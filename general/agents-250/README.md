# Agents

> This guide shows you how to set up and use LangGraph's **prebuilt**, **reusable** components, which are designed to help you construct agentic systems quickly and reliably.

## Model
- **Default:** `claude-sonnet-4-5`

## Tags
`agent`

## System Prompt
# LangGraph quickstart

This guide shows you how to set up and use LangGraph's **prebuilt**, **reusable** components, which are designed to help you construct agentic systems quickly and reliably.

## Prerequisites

Before you start this tutorial, ensure you have the following:

- An [Anthropic](https://console.anthropic.com/settings/keys) API key

## 1. Install dependencies

If you haven't already, install LangGraph and LangChain:

:::python

```
pip install -U langgraph "langchain[anthropic]"
```

!!! info

    `langchain[anthropic]` is installed so the agent can call the [model](https://python.langchain.com/docs/integrations/chat/).

:::

:::js

```bash
npm install @langchain/langgraph @langchain/core @langchain/anthropic
```

!!! info

    `@langchain/core` `@langchain/anthropic` are installed so the agent can call the [model](https://js.langchain.com/docs/integrations/chat/).

:::

## 2. Create an agent

:::python
To create an agent, use @[`create_react_agent`][create_react_agent]:

```python
from langgraph.prebuilt import create_react_agent

def get_weather(city: str) -> str:  # (1)!
    """Get weather for a given city."""
    return f"It's always sunny in {city}!"

agent = create_react_agent(
    model="anthropic:claude-3-7-sonnet-latest",  # (2)!
    tools=[get_weather],  # (3)!
    prompt="You are a helpful assistant"  # (4)!
)

# Run the agent
agent.invoke(
    {"messages": [{"role": "user", "content": "what is the weather in sf"}]}
)
```

1. Define a tool for the agent to use. Tools can be defined as vanilla Python functions. For more advanced tool usage and customization, check the [tools](../how-tos/tool-calling.md) page.
2. Provide a language model for the agent to use. To learn more about configuring language models for the agents, check the [models](./models.md) page.
3. Provide a list of tools for the model to use.
4. Provide a system prompt (instructions) to the language model used by the agent.
   :::

:::js
To create an agent, use [`createReactAg

*[truncated — see source for full prompt]*