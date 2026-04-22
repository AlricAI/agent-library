# Handle Parsing Errors

> Il arrive parfois que le LLM ne puisse pas déterminer quelle étape suivre car ses sorties ne sont pas correctement formatées pour être gérées par l'analyseur de sortie.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Gérer les erreurs d'analyse

Il arrive parfois que le LLM ne puisse pas déterminer quelle étape suivre car ses sorties ne sont pas correctement formatées pour être gérées par l'analyseur de sortie. Dans ce cas, par défaut, l'agent génère une erreur. Mais vous pouvez facilement contrôler cette fonctionnalité avec `handle_parsing_errors` ! Explorons comment.

## Configuration

Nous allons utiliser un outil wikipedia, donc nous devons l'installer.

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

## Erreur

Dans ce scénario, l'agent générera une erreur car il ne parvient pas à produire une chaîne d'action (ce que nous l'avons piégé à faire avec une entrée malveillante).

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
->

*[truncated — see source for full prompt]*