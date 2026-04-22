# Agent Structured

> Ce notebook couvre comment faire en sorte qu'un agent renvoie un résultat structuré.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Retour d'un résultat structuré

Ce notebook couvre comment faire en sorte qu'un agent renvoie un résultat structuré.
Par défaut, la plupart des agents renvoient une seule chaîne de caractères.
Il peut souvent être utile d'avoir un agent qui renvoie quelque chose avec plus de structure.

Un bon exemple de cela est un agent chargé de faire de la réponse aux questions sur certaines sources.
Supposons que nous voulions que l'agent réponde non seulement avec la réponse, mais aussi avec une liste des sources utilisées.
Nous voulons alors que notre sortie suive approximativement le schéma ci-dessous :

```python
class Response(BaseModel):
    """Final response to the question being asked"""
    answer: str = Field(description = "The final answer to respond to the user")
    sources: List[int] = Field(description="List of page chunks that contain answer to the question. Only include a page chunk if it contains relevant information")
```

Dans ce notebook, nous allons passer en revue un agent qui a un outil de recherche et qui répond dans le bon format.

## Créer le moteur de recherche

Dans cette section, nous allons effectuer quelques travaux de configuration pour créer notre moteur de recherche sur des données factices contenant le "discours sur l'état de l'Union". Fait important, nous ajouterons une balise "page_chunk" aux métadonnées de chaque document. Il s'agit simplement de données factices destinées à simuler un champ source. En pratique, il s'agirait plus probablement de l'URL ou du chemin d'un document.

```python
%pip install -qU langchain langchain-community langchain-openai langchain-chroma
```

```python
from langchain_chroma import Chroma
from langchain_community.document_loaders import TextLoader
from langchain_openai import OpenAIEmbeddings
from langchain_text_splitters import RecursiveCharacterTextSplitter
```

```python
# Load in document to retrieve over
loader = TextLoader("../../state_of_the_union.txt")
documents = loader.load()

# Split document int

*[truncated — see source for full prompt]*