# Xml Agent

> Algunos modelos de lenguaje (como el de Anthropic, Claude) son particularmente buenos en el razonamiento/escritura de XML.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agente XML

Algunos modelos de lenguaje (como el de Anthropic, Claude) son particularmente buenos en el razonamiento/escritura de XML. Esto explica cómo usar un agente que utiliza XML al solicitar.

:::tip

* Usar con LLM regulares, no con modelos de chat.
* Usar solo con herramientas no estructuradas; es decir, herramientas que aceptan una sola entrada de cadena.
* Consultar la documentación de [AgentTypes](/docs/modules/agents/agent_types/) para obtener más tipos de agentes.
:::

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_xml_agent
from langchain_anthropic.chat_models import ChatAnthropic
from langchain_community.tools.tavily_search import TavilySearchResults
```

## Inicializar herramientas

Inicializaremos las herramientas que queremos usar.

```python
tools = [TavilySearchResults(max_results=1)]
```

## Crear agente

A continuación, usaremos el constructor [create_xml_agent](https://api.python.langchain.com/en/latest/agents/langchain.agents.xml.base.create_xml_agent.html) incorporado en LangChain.

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

## Ejecutar agente

```python
# Create an agent executor by passing in the agent and tools
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

```python
agent_executor.invoke({"input": "what is LangChain?"})
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m <tool>tavily_search_results_json</tool><tool_input>what is LangChain?[0m[36;1m[1;3m[{'url': 'https://aws.amazon.com/what-is/langchain/', 'content': 'What Is LangChain? What is LangChain?  How does LangChain work?  Why is LangChain important?  that LangChain provides to reduce development time.LangChain is an open source framework for building

*[truncated — see source for full prompt]*