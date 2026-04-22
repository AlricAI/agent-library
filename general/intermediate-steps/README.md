# Intermediate Steps

> एक एजेंट क्या कर रहा है, इसके बारे में अधिक दृश्यता प्राप्त करने के लिए, हम मध्यवर्ती चरणों को भी वापस कर सकते हैं। यह रिटर्न मूल्य में एक अतिरिक्त कु

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# मध्यवर्ती चरणों का प्रवेश

एक एजेंट क्या कर रहा है, इसके बारे में अधिक दृश्यता प्राप्त करने के लिए, हम मध्यवर्ती चरणों को भी वापस कर सकते हैं। यह रिटर्न मूल्य में एक अतिरिक्त कुंजी के रूप में आता है, जो (कार्रवाई, अवलोकन) ट्यूपल की एक सूची है।

```python
# pip install wikipedia
```

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_openai_functions_agent
from langchain_community.tools import WikipediaQueryRun
from langchain_community.utilities import WikipediaAPIWrapper
from langchain_openai import ChatOpenAI

api_wrapper = WikipediaAPIWrapper(top_k_results=1, doc_content_chars_max=100)
tool = WikipediaQueryRun(api_wrapper=api_wrapper)
tools = [tool]

# Get the prompt to use - you can modify this!
# If you want to see the prompt in full, you can at: https://smith.langchain.com/hub/hwchase17/openai-functions-agent
prompt = hub.pull("hwchase17/openai-functions-agent")

llm = ChatOpenAI(temperature=0)

agent = create_openai_functions_agent(llm, tools, prompt)
```

`return_intermediate_steps=True` के साथ AgentExecutor को प्रारंभ करें:

```python
agent_executor = AgentExecutor(
    agent=agent, tools=tools, verbose=True, return_intermediate_steps=True
)
```

```python
response = agent_executor.invoke({"input": "What is Leo DiCaprio's middle name?"})
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m
Invoking: `Wikipedia` with `Leo DiCaprio`


[0m[36;1m[1;3mPage: Leonardo DiCaprio
Summary: Leonardo Wilhelm DiCaprio (; Italian: [diˈkaːprjo]; born November 1[0m[32;1m[1;3mLeonardo DiCaprio's middle name is Wilhelm.[0m

[1m> Finished chain.[0m
```

```python
# The actual return type is a NamedTuple for the agent action, and then an observation
print(response["intermediate_steps"])
```

```output
[(AgentActionMessageLog(tool='Wikipedia', tool_input='Leo DiCaprio', log='\nInvoking: `Wikipedia` with `Leo DiCaprio`\n\n\n', message_log=[AIMessage(content='', additional_kwargs={'function_call': {'name': 'Wiki

*[truncated — see source for full prompt]*