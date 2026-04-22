# Openai Tools

> Los modelos más recientes de OpenAI se han ajustado con precisión para detectar cuándo se debe(n) llamar una o más funciones y responder con los datos que se deben pasar a la(s) función(es).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Herramientas de OpenAI

Los modelos más recientes de OpenAI se han ajustado con precisión para detectar cuándo se debe(n) llamar una o más funciones y responder con los datos que se deben pasar a la(s) función(es). En una llamada a la API, puede describir funciones y hacer que el modelo elija inteligentemente generar un objeto JSON que contenga los argumentos para llamar a estas funciones. El objetivo de las API de herramientas de OpenAI es devolver llamadas de función más confiables y útiles de lo que se puede hacer con una API de texto genérica o de chat.

OpenAI denominó la capacidad de invocar una **sola** función como **funciones**, y la capacidad de invocar **una o más** funciones como **herramientas**.

:::tip

En la API de chat de OpenAI, las **funciones** ahora se consideran una opción heredada que está en desuso a favor de las **herramientas**.

Si está creando agentes utilizando modelos de OpenAI, debe usar este agente de herramientas de OpenAI en lugar del agente de funciones de OpenAI.

El uso de **herramientas** permite que el modelo solicite que se llame a más de una función cuando sea apropiado.

En algunas situaciones, esto puede ayudar a reducir significativamente el tiempo que le toma a un agente lograr su objetivo.

Ver

* [Crear chat de OpenAI](https://platform.openai.com/docs/api-reference/chat/create)
* [Llamada de función de OpenAI](https://platform.openai.com/docs/guides/function-calling)

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

## Inicializar herramientas

Para este agente, vamos a darle la capacidad de buscar en la web con Tavily.

```python
tools = [TavilySearchResults(max_results=1)]
```

## Crear agente

```python
# Get the prompt to use - you can modify this!
prompt = hub.

*[truncated — see source for full prompt]*