# Agent Iter

> Il peut être utile d'exécuter l'agent en tant qu'itérateur, pour ajouter des vérifications avec l'humain dans la boucle si nécessaire.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Exécuter l'agent en tant qu'itérateur

Il peut être utile d'exécuter l'agent en tant qu'itérateur, pour ajouter des vérifications avec l'humain dans la boucle si nécessaire.

Pour démontrer les fonctionnalités de `AgentExecutorIterator`, nous allons configurer un problème où un agent doit :

- Récupérer trois nombres premiers à partir d'un outil
- Les multiplier ensemble.

Dans ce problème simple, nous pouvons démontrer l'ajout d'une logique pour vérifier les étapes intermédiaires en vérifiant si leurs sorties sont des nombres premiers.

```python
from langchain.agents import AgentType, initialize_agent
from langchain.chains import LLMMathChain
from langchain_core.pydantic_v1 import BaseModel, Field
from langchain_core.tools import Tool
from langchain_openai import ChatOpenAI
```

```python
%pip install --upgrade --quiet  numexpr
```

```python
# need to use GPT-4 here as GPT-3.5 does not understand, however hard you insist, that
# it should use the calculator to perform the final calculation
llm = ChatOpenAI(temperature=0, model="gpt-4")
llm_math_chain = LLMMathChain.from_llm(llm=llm, verbose=True)
```

Définir les outils qui fournissent :

- Le `n`ième nombre premier (en utilisant un petit sous-ensemble pour cet exemple)

- La `LLMMathChain` pour agir en tant que calculatrice

```python
primes = {998: 7901, 999: 7907, 1000: 7919}


class CalculatorInput(BaseModel):
    question: str = Field()


class PrimeInput(BaseModel):
    n: int = Field()


def is_prime(n: int) -> bool:
    if n <= 1 or (n % 2 == 0 and n > 2):
        return False
    for i in range(3, int(n**0.5) + 1, 2):
        if n % i == 0:
            return False
    return True


def get_prime(n: int, primes: dict = primes) -> str:
    return str(primes.get(int(n)))


async def aget_prime(n: int, primes: dict = primes) -> str:
    return str(primes.get(int(n)))


tools = [
    Tool(
        name="GetPrime",
        func=get_prime,
        description="A tool that returns the `n`th prime number",
   

*[truncated — see source for full prompt]*