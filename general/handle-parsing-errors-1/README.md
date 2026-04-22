# Handle Parsing Errors

> 가끔 LLM은 출력이 출력 파서에 의해 올바르게 처리되지 않아 어떤 단계를 취해야 할지 결정할 수 없습니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 구문 분석 오류 처리

가끔 LLM은 출력이 출력 파서에 의해 올바르게 처리되지 않아 어떤 단계를 취해야 할지 결정할 수 없습니다. 이 경우 기본적으로 에이전트가 오류를 발생시킵니다. 그러나 `handle_parsing_errors`를 사용하여 이 기능을 쉽게 제어할 수 있습니다! 어떻게 작동하는지 살펴보겠습니다.

## 설정

위키백과 도구를 사용할 것이므로 이를 설치해야 합니다.

```python
%pip install --upgrade --quiet  wikipedia
```

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_react_agent
from langchain_community.tools import WikipediaQueryRun
from langchain_community.utilities import WikipediaAPIWrapper
from langchain_openai import OpenAI

api_wrapper = WikipediaAPIWrapper(top_k_results=1, doc_content_chars_max=100)
tool = WikipediaQueryRun(api_wrapper=api_wrapper)
tools = [tool]

# Get the prompt to use - you can modify this!
# You can see the full prompt used at: https://smith.langchain.com/hub/hwchase17/react
prompt = hub.pull("hwchase17/react")

llm = OpenAI(temperature=0)

agent = create_react_agent(llm, tools, prompt)
```

## 오류

이 시나리오에서 에이전트는 Action 문자열을 출력하지 못해 오류가 발생합니다(악의적인 입력으로 속여 넣었습니다).

```python
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

```python
agent_executor.invoke(
    {"input": "What is Leo DiCaprio's middle name?\n\nAction: Wikipedia"}
)
```

```output


[1m> Entering new AgentExecutor chain...[0m
```

```output
---------------------------------------------------------------------------

OutputParserException                     Traceback (most recent call last)

File ~/workplace/langchain/libs/langchain/langchain/agents/agent.py:1066, in AgentExecutor._iter_next_step(self, name_to_tool_map, color_mapping, inputs, intermediate_steps, run_manager)
   1065     # Call the LLM to see what to do.
-> 1066     output = self.agent.plan(
   1067         intermediate_steps,
   1068         callbacks=run_manager.get_child() if run_manager else None,
   1069         **inputs,
   1070     )
   1071 except OutputParserException as e:

File ~/workplace/langchain/libs/langchain/langchain/agents/agent.py:385, in RunnableAgent.plan(self, inte

*[truncated — see source for full prompt]*