# Agent Iter

> एजेंट को एक इटरेटर के रूप में चलाना उपयोगी हो सकता है, जहां आवश्यकतानुसार मानव-में-लूप जांच जोड़ी जा सकती है।

`AgentExecutorIterator` कार्यक्षमता का 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# एजेंट को एक इटरेटर के रूप में चलाना

एजेंट को एक इटरेटर के रूप में चलाना उपयोगी हो सकता है, जहां आवश्यकतानुसार मानव-में-लूप जांच जोड़ी जा सकती है।

`AgentExecutorIterator` कार्यक्षमता का प्रदर्शन करने के लिए, हम एक ऐसी समस्या सेट अप करेंगे जहां एक एजेंट को:

- एक टूल से तीन प्राइम नंबर प्राप्त करना होगा
- इन्हें एक साथ गुणा करना होगा।

इस सरल समस्या में हम मध्यवर्ती चरणों की जांच करने के लिए कुछ तर्क जोड़कर दिखा सकते हैं कि क्या उनके आउटपुट प्राइम हैं।

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

उन टूल्स को परिभाषित करें जो प्रदान करते हैं:

- `n`वां प्राइम नंबर (इस उदाहरण के लिए एक छोटे सेट का उपयोग करते हुए)

- गणना करने के लिए `LLMMathChain`

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
        args_schema=PrimeInput,
        coroutine=aget_prime,
    ),
    Tool.from_function(
        func=llm_math

*[truncated — see source for full prompt]*