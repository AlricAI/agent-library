# Custom Agent

> Ce cahier de notes explique comment créer votre propre agent personnalisé.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent personnalisé

Ce cahier de notes explique comment créer votre propre agent personnalisé.

Dans cet exemple, nous utiliserons OpenAI Tool Calling pour créer cet agent.
**C'est généralement le moyen le plus fiable de créer des agents.**

Nous le créerons d'abord SANS mémoire, puis nous montrerons comment y ajouter de la mémoire.
La mémoire est nécessaire pour permettre la conversation.

## Charger le modèle de langage

Tout d'abord, chargeons le modèle de langage que nous allons utiliser pour contrôler l'agent.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo", temperature=0)
```

## Définir les outils

Ensuite, définissons quelques outils à utiliser.
Écrivons une fonction Python très simple pour calculer la longueur d'un mot qui lui est passé.

Notez que la docstring de la fonction que nous utilisons est assez importante ici. Lisez-en plus sur les raisons [ici](/docs/modules/tools/custom_tools)

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

## Créer l'invite

Maintenant, créons l'invite.
Comme OpenAI Function Calling est affiné pour l'utilisation d'outils, nous n'avons presque pas besoin d'instructions sur la façon de raisonner ou de formater la sortie.
Nous n'aurons que deux variables d'entrée : `input` et `agent_scratchpad`. `input` doit être une chaîne contenant l'objectif de l'utilisateur. `agent_scratchpad` doit être une séquence de messages contenant les invocations d'outils précédentes de l'agent et les sorties d'outils correspondantes.

```python
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are very powerful assistant, but don't know current events",
        ),
        ("user", "{input}"

*[truncated — see source for full prompt]*