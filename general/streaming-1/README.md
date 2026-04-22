# Streaming

> Le streaming est une considération importante pour l'expérience utilisateur des applications d'apprentissage automatique de langage (LLM), et les agents n'y font pas exception.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Streaming

Le streaming est une considération importante pour l'expérience utilisateur des applications d'apprentissage automatique de langage (LLM), et les agents n'y font pas exception. Le streaming avec les agents est rendu plus complexe par le fait que ce n'est pas seulement les jetons de la réponse finale que vous voudrez diffuser en continu, mais vous voudrez également diffuser en continu les étapes intermédiaires que l'agent entreprend.

Dans ce notebook, nous aborderons les `stream/astream` et `astream_events` pour le streaming.

Notre agent utilisera une API d'outils pour l'invocation d'outils avec les outils suivants :

1. `where_cat_is_hiding` : Renvoie un endroit où le chat se cache
2. `get_items` : Répertorie les articles qui peuvent être trouvés dans un endroit particulier

Ces outils nous permettront d'explorer le streaming dans une situation plus intéressante où l'agent devra utiliser les deux outils pour répondre à certaines questions (par exemple, pour répondre à la question "Quels articles se trouvent là où le chat se cache ?").

Prêt ?🏎️

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_openai_tools_agent
from langchain.tools import tool
from langchain_core.callbacks import Callbacks
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
```

## Créer le modèle

**Attention** Nous définissons `streaming=True` sur le LLM. Cela nous permettra de diffuser en continu les jetons de l'agent à l'aide de l'API `astream_events`. C'est nécessaire pour les anciennes versions de LangChain.

```python
model = ChatOpenAI(temperature=0, streaming=True)
```

## Outils

Nous définissons deux outils qui s'appuient sur un modèle de discussion pour générer la sortie !

```python
import random


@tool
async def where_cat_is_hiding() -> str:
    """Where is the cat hiding right now?"""
    return random.choice(["under the bed", "on the shelf"])


@tool
async def get_items(place: str) -> st

*[truncated — see source for full prompt]*