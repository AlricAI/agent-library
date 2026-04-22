# Xml Agent

> Some language models (like Anthropic's Claude) are particularly good at reasoning/writing XML.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# XML Agent

Some language models (like Anthropic's Claude) are particularly good at reasoning/writing XML. This goes over how to use an agent that uses XML when prompting.

:::tip

* Use with regular LLMs, not with chat models.
* Use only with unstructured tools; i.e., tools that accept a single string input.
* See [AgentTypes](/docs/modules/agents/agent_types/) documentation for more agent types.
:::

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_xml_agent
from langchain_anthropic.chat_models import ChatAnthropic
from langchain_community.tools.tavily_search import TavilySearchResults
```

## Initialize Tools

We will initialize the tools we want to use

```python
tools = [TavilySearchResults(max_results=1)]
```

## Create Agent

Below we will use LangChain's built-in [create_xml_agent](https://api.python.langchain.com/en/latest/agents/langchain.agents.xml.base.create_xml_agent.html) constructor.

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/xml-agent-convo")
```

```python
# Choose the LLM that will drive the agent
llm = ChatAnthropic(model="claude-2.1")

# Construct the XML agent
agent = create_xml_agent(llm, tools, prompt)
```

## Run Agent

```python
# Create an agent executor by passing in the agent and tools
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

```python
agent_executor.invoke({"input": "what is LangChain?"})
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m <tool>tavily_search_results_json</tool><tool_input>what is LangChain?[0m[36;1m[1;3m[{'url': 'https://aws.amazon.com/what-is/langchain/', 'content': 'What Is LangChain? What is LangChain?  How does LangChain work?  Why is LangChain important?  that LangChain provides to reduce development time.LangChain is an open source framework for building applications based on large language models (LLMs). LLMs are large deep-learning models pre-trained on large amounts 

*[truncated — see source for full prompt]*