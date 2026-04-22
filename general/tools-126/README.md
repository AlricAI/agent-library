# Tools

> Having proper tool abstractions is at the core of building [agentic systems in LlamaIndex](/python/framework/module_guides/deploying/agents).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Concept

Having proper tool abstractions is at the core of building [agentic systems in LlamaIndex](/python/framework/module_guides/deploying/agents). Defining a set of Tools is similar to defining any API interface, with the exception that these Tools are meant for agent rather than human use. We allow users to define both a **Tool** as well as a **ToolSpec** containing a series of functions under the hood.

When using an agent or LLM with function calling, the tool selected (and the arguments written for that tool) rely strongly on the **tool name** and **description** of the tools purpose and arguments. Spending time tuning these parameters can result in larges changes in how the LLM calls these tools.

A Tool implements a very generic interface - simply define `__call__` and also return some basic metadata (name, description, function schema).

We offer a few different types of Tools:

- `FunctionTool`: A function tool allows users to easily convert any user-defined function into a Tool. It can also auto-infer the function schema, or let you customize various aspects.
- `QueryEngineTool`: A tool that wraps an existing [query engine](/python/framework/module_guides/deploying/query_engine). Note: since our agent abstractions inherit from `BaseQueryEngine`, these tools can also wrap other agents.
- Community contributed `ToolSpecs` that define one or more tools around a single service (like Gmail)
- Utility tools for wrapping other tools to handle returning large amounts of data from a tool

## FunctionTool

A function tool is a simple wrapper around any existing function (both sync and async are supported!).

```python
from llama_index.core.agent.workflow import ReActAgent
from llama_index.core.tools import FunctionTool


def get_weather(location: str) -> str:
    """Usfeful for getting the weather for a given location."""
    ...


tool = FunctionTool.from_defaults(
    get_weather,
    # async_fn=aget_weather,  # optional!
)

agent = ReActAgent(llm=llm, tools

*[truncated — see source for full prompt]*