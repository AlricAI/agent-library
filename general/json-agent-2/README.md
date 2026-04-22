# Json Agent

> 일부 언어 모델은 JSON 작성에 특히 능합니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# JSON 채팅 에이전트

일부 언어 모델은 JSON 작성에 특히 능합니다. 이 에이전트는 JSON을 사용하여 출력을 형식화하며, 채팅 모델을 지원하는 것을 목표로 합니다.

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_json_chat_agent
from langchain_community.tools.tavily_search import TavilySearchResults
from langchain_openai import ChatOpenAI
```

## 도구 초기화

우리가 사용하고자 하는 도구를 초기화할 것입니다.

```python
tools = [TavilySearchResults(max_results=1)]
```

## 에이전트 생성

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/react-chat-json")
```

```python
# Choose the LLM that will drive the agent
llm = ChatOpenAI()

# Construct the JSON agent
agent = create_json_chat_agent(llm, tools, prompt)
```

## 에이전트 실행

```python
# Create an agent executor by passing in the agent and tools
agent_executor = AgentExecutor(
    agent=agent, tools=tools, verbose=True, handle_parsing_errors=True
)
```

```python
agent_executor.invoke({"input": "what is LangChain?"})
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m{
    "action": "tavily_search_results_json",
    "action_input": "LangChain"
}[0m[36;1m[1;3m[{'url': 'https://www.ibm.com/topics/langchain', 'content': 'LangChain is essentially a library of abstractions for Python and Javascript, representing common steps and concepts  LangChain is an open source orchestration framework for the development of applications using large language models  other LangChain features, like the eponymous chains.  LangChain provides integrations for over 25 different embedding methods, as well as for over 50 different vector storesLangChain is a tool for building applications using large language models (LLMs) like chatbots and virtual agents. It simplifies the process of programming and integration with external data sources and software workflows. It supports Python and Javascript languages and supports various LLM providers, including OpenAI, Google, and IBM.'}][0m[32;1m[1;3m{
    "action": "Final Answer",
    "action_inpu

*[truncated — see source for full prompt]*