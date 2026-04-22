# Custom Agent

> Este cuaderno explica cómo crear tu propio agente personalizado.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agente personalizado

Este cuaderno explica cómo crear tu propio agente personalizado.

En este ejemplo, utilizaremos OpenAI Tool Calling para crear este agente.
**Esta es generalmente la forma más confiable de crear agentes.**

Primero lo crearemos SIN memoria, pero luego mostraremos cómo agregar memoria.
La memoria es necesaria para habilitar la conversación.

## Cargar el modelo de lenguaje

Primero, carguemos el modelo de lenguaje que vamos a utilizar para controlar el agente.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo", temperature=0)
```

## Definir herramientas

A continuación, definamos algunas herramientas para usar.
Escribiremos una función de Python realmente simple para calcular la longitud de una palabra que se pasa como argumento.

Tenga en cuenta que aquí la cadena de documentación de la función que usamos es bastante importante. Lea más sobre por qué es el caso [aquí](/docs/modules/tools/custom_tools)

```python
from langchain.agents import tool


@tool
def get_word_length(word: str) -> int:
    """Returns the length of a word."""
    return len(word)


get_word_length.invoke("abc")
```

```output
3
```

```python
tools = [get_word_length]
```

## Crear el prompt

Ahora creemos el prompt.
Dado que OpenAI Function Calling está entrenado específicamente para el uso de herramientas, apenas necesitamos instrucciones sobre cómo razonar o cómo dar formato a la salida.
Tendremos dos variables de entrada: `input` y `agent_scratchpad`. `input` debe ser una cadena que contenga el objetivo del usuario. `agent_scratchpad` debe ser una secuencia de mensajes que contenga las invocaciones previas de herramientas del agente y las salidas correspondientes.

```python
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are very powerful assistant, but don't know current events",
        ),
        ("

*[truncated — see source for full prompt]*