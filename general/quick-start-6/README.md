# Quick Start

> Pour mieux comprendre le cadre des agents, construisons un agent qui a deux outils : l'un pour rechercher des choses en ligne et l'autre pour recherch

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Démarrage rapide

Pour mieux comprendre le cadre des agents, construisons un agent qui a deux outils : l'un pour rechercher des choses en ligne et l'autre pour rechercher des données spécifiques que nous avons chargées dans un index.

Cela supposera une connaissance des [LLM](/docs/modules/model_io/) et de la [récupération](/docs/modules/data_connection/), donc si vous n'avez pas encore exploré ces sections, il est recommandé de le faire.

## Configuration : LangSmith

Par définition, les agents prennent une séquence d'étapes auto-déterminée et dépendante des entrées avant de renvoyer une sortie destinée à l'utilisateur. Cela rend le débogage de ces systèmes particulièrement délicat et l'observabilité particulièrement importante. [LangSmith](/docs/langsmith) est particulièrement utile dans ces cas.

Lors de la construction avec LangChain, toutes les étapes seront automatiquement tracées dans LangSmith.
Pour configurer LangSmith, nous devons simplement définir les variables d'environnement suivantes :

```bash
export LANGCHAIN_TRACING_V2="true"
export LANGCHAIN_API_KEY="<your-api-key>"
```

## Définir les outils

Nous devons d'abord créer les outils que nous voulons utiliser. Nous utiliserons deux outils : [Tavily](/docs/integrations/tools/tavily_search) (pour rechercher en ligne) et ensuite un récupérateur sur un index local que nous créerons.

### [Tavily](/docs/integrations/tools/tavily_search)

Nous avons un outil intégré dans LangChain pour utiliser facilement le moteur de recherche Tavily comme outil.
Notez que cela nécessite une clé API - ils ont un niveau gratuit, mais si vous n'en avez pas ou ne voulez pas en créer une, vous pouvez toujours ignorer cette étape.

Une fois que vous avez créé votre clé API, vous devrez l'exporter en tant que :

```bash
export TAVILY_API_KEY="..."
```

```python
from langchain_community.tools.tavily_search import TavilySearchResults
```

```python
search = TavilySearchResults()
```

```python
search.invoke("what is the weather

*[truncated — see source for full prompt]*