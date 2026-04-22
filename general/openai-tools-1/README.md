# Openai Tools

> Newer OpenAI models have been fine-tuned to detect when **one or more** function(s) should be called and respond with the inputs that should be passed to the function(s).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAI tools

Newer OpenAI models have been fine-tuned to detect when **one or more** function(s) should be called and respond with the inputs that should be passed to the function(s). In an API call, you can describe functions and have the model intelligently choose to output a JSON object containing arguments to call these functions. The goal of the OpenAI tools APIs is to more reliably return valid and useful function calls than what can be done using a generic text completion or chat API.

OpenAI termed the capability to invoke a **single** function as **functions**, and the capability to invoke **one or more** functions as **tools**.

:::tip

In the OpenAI Chat API, **functions** are now considered a legacy options that is deprecated in favor of **tools**.

If you're creating agents using OpenAI models, you should be using this OpenAI Tools agent rather than the OpenAI functions agent.

Using **tools** allows the model to request that more than one function will be called upon when appropriate.

In some situations, this can help signficantly reduce the time that it takes an agent to achieve its goal.

See

* [OpenAI chat create](https://platform.openai.com/docs/api-reference/chat/create)
* [OpenAI function calling](https://platform.openai.com/docs/guides/function-calling)

:::

```python
%pip install --upgrade --quiet  langchain-openai tavily-python
```

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_openai_tools_agent
from langchain_community.tools.tavily_search import TavilySearchResults
from langchain_openai import ChatOpenAI
```

## Initialize Tools

For this agent let's give it the ability to search the web with Tavily.

```python
tools = [TavilySearchResults(max_results=1)]
```

## Create Agent

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/openai-tools-agent")
```

```python
# Choose the LLM that will drive the agent
# Only certain models support this
llm = ChatOpenAI(model

*[truncated — see source for full prompt]*