# Tool Calling

> [Tool calling](/docs/modules/model_io/chat/function_calling) allows a model to detect when one or more tools should be called and respond with the inputs that should be passed to those tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tool calling agent

[Tool calling](/docs/modules/model_io/chat/function_calling) allows a model to detect when one or more tools should be called and respond with the inputs that should be passed to those tools. In an API call, you can describe tools and have the model intelligently choose to output a structured object like JSON containing arguments to call these tools. The goal of tools APIs is to more reliably return valid and useful tool calls than what can be done using a generic text completion or chat API.

We can take advantage of this structured output, combined with the fact that you can bind multiple tools to a [tool calling chat model](/docs/integrations/chat/) and
allow the model to choose which one to call, to create an agent that repeatedly calls tools and receives results until a query is resolved.

This is a more generalized version of the [OpenAI tools agent](/docs/modules/agents/agent_types/openai_tools/), which was designed for OpenAI's specific style of
tool calling. It uses LangChain's ToolCall interface to support a wider range of
provider implementations, such as [Anthropic](/docs/integrations/chat/anthropic/), [Google Gemini](/docs/integrations/chat/google_vertex_ai_palm/), and [Mistral](/docs/integrations/chat/mistralai/)
in addition to [OpenAI](/docs/integrations/chat/openai/).

## Setup

Any models that support tool calling can be used in this agent. You can see which models support tool calling [here](/docs/integrations/chat/)

This demo uses [Tavily](https://app.tavily.com), but you can also swap in any other [built-in tool](/docs/integrations/tools) or add [custom tools](/docs/modules/tools/custom_tools/).
You'll need to sign up for an API key and set it as `process.env.TAVILY_API_KEY`.

import ChatModelTabs from "@theme/ChatModelTabs";

<ChatModelTabs
  customVarName="llm"
  hideCohere
/>

```python
# | output: false
# | echo: false

from langchain_anthropic import ChatAnthropic

llm = ChatAnthropic(model="claude-3-sonnet-20240229", 

*[truncated — see source for full prompt]*