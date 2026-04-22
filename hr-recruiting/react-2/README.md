# React

> This walkthrough showcases using an agent to implement the [ReAct](https://react-lm.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ReAct

This walkthrough showcases using an agent to implement the [ReAct](https://react-lm.github.io/) logic.

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_react_agent
from langchain_community.tools.tavily_search import TavilySearchResults
from langchain_openai import OpenAI
```

## Initialize tools

Let's load some tools to use.

```python
tools = [TavilySearchResults(max_results=1)]
```

## Create Agent

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/react")
```

```python
# Choose the LLM to use
llm = OpenAI()

# Construct the ReAct agent
agent = create_react_agent(llm, tools, prompt)
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
[32;1m[1;3m I should research LangChain to learn more about it.
Action: tavily_search_results_json
Action Input: "LangChain"[0m[36;1m[1;3m[{'url': 'https://www.ibm.com/topics/langchain', 'content': 'LangChain is essentially a library of abstractions for Python and Javascript, representing common steps and concepts  LangChain is an open source orchestration framework for the development of applications using large language models  other LangChain features, like the eponymous chains.  LangChain provides integrations for over 25 different embedding methods, as well as for over 50 different vector storesLangChain is a tool for building applications using large language models (LLMs) like chatbots and virtual agents. It simplifies the process of programming and integration with external data sources and software workflows. It supports Python and Javascript languages and supports various LLM providers, including OpenAI, Google, and IBM.'}][0m[32;1m[1;3m I should read the summary and look at the different featur

*[truncated — see source for full prompt]*