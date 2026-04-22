# Xml Agent

> Certains modèles de langage (comme Claude d'Anthropic) sont particulièrement performants pour le raisonnement/l'écriture en XML.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent XML

Certains modèles de langage (comme Claude d'Anthropic) sont particulièrement performants pour le raisonnement/l'écriture en XML. Ceci explique comment utiliser un agent qui utilise XML lors de la sollicitation.

:::tip

* À utiliser avec des LLM réguliers, pas avec des modèles de chat.
* À utiliser uniquement avec des outils non structurés ; c'est-à-dire des outils qui acceptent une seule entrée sous forme de chaîne de caractères.
* Consultez la documentation [AgentTypes](/docs/modules/agents/agent_types/) pour plus de types d'agents.
:::

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_xml_agent
from langchain_anthropic.chat_models import ChatAnthropic
from langchain_community.tools.tavily_search import TavilySearchResults
```

## Initialiser les outils

Nous allons initialiser les outils que nous voulons utiliser.

```python
tools = [TavilySearchResults(max_results=1)]
```

## Créer un agent

Ci-dessous, nous utiliserons le constructeur intégré [create_xml_agent](https://api.python.langchain.com/en/latest/agents/langchain.agents.xml.base.create_xml_agent.html) de LangChain.

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

## Exécuter l'agent

```python
# Create an agent executor by passing in the agent and tools
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

```python
agent_executor.invoke({"input": "what is LangChain?"})
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m <tool>tavily_search_results_json</tool><tool_input>what is LangChain?[0m[36;1m[1;3m[{'url': 'https://aws.amazon.com/what-is/langchain/', 'content': 'What Is LangChain? What is LangChain?  How does LangChain work?  Why is LangChain important?  that LangChain prov

*[truncated — see source for full prompt]*