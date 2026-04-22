# Tool Calling

> [Llamada de herramienta](/docs/modules/model_io/chat/function_calling) permite que un modelo detecte cuándo se deben llamar una o más herramientas y r

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agente de llamada de herramienta

[Llamada de herramienta](/docs/modules/model_io/chat/function_calling) permite que un modelo detecte cuándo se deben llamar una o más herramientas y responda con las entradas que se deben pasar a esas herramientas. En una llamada a la API, puede describir herramientas y hacer que el modelo elija inteligentemente generar un objeto estructurado como JSON que contenga argumentos para llamar a estas herramientas. El objetivo de las API de herramientas es devolver llamadas de herramientas más confiables y útiles de lo que se puede hacer usando una API de texto genérico o de chat.

Podemos aprovechar esta salida estructurada, combinada con el hecho de que puede vincular varias herramientas a un [modelo de chat de llamada de herramienta](/docs/integrations/chat/) y permitir que el modelo elija cuál llamar, para crear un agente que llame repetidamente a herramientas y reciba resultados hasta que se resuelva una consulta.

Esta es una versión más generalizada del [agente de herramientas de OpenAI](/docs/modules/agents/agent_types/openai_tools/), que fue diseñado para el estilo específico de llamada de herramientas de OpenAI. Utiliza la interfaz ToolCall de LangChain para admitir una gama más amplia de implementaciones de proveedores, como [Anthropic](/docs/integrations/chat/anthropic/), [Google Gemini](/docs/integrations/chat/google_vertex_ai_palm/) y [Mistral](/docs/integrations/chat/mistralai/) además de [OpenAI](/docs/integrations/chat/openai/).

## Configuración

Cualquier modelo que admita la llamada de herramientas se puede usar en este agente. Puede ver qué modelos admiten la llamada de herramientas [aquí](/docs/integrations/chat/)

Esta demostración usa [Tavily](https://app.tavily.com), pero también puede intercambiar cualquier otra [herramienta incorporada](/docs/integrations/tools) o agregar [herramientas personalizadas](/docs/modules/tools/custom_tools/).
Deberá registrarse para obtener una clave API y establecerla como `process

*[truncated — see source for full prompt]*