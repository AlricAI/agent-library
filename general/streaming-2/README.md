# Streaming

> 스트리밍은 LLM 앱의 중요한 UX 고려사항이며, 에이전트도 예외는 아닙니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 스트리밍

스트리밍은 LLM 앱의 중요한 UX 고려사항이며, 에이전트도 예외는 아닙니다. 에이전트에서의 스트리밍은 최종 답변의 토큰뿐만 아니라 에이전트가 수행하는 중간 단계도 스트리밍하고 싶을 수 있다는 점에서 더 복잡해집니다.

이 노트북에서는 스트리밍을 위한 `stream/astream` 및 `astream_events`를 다룰 것입니다.

우리의 에이전트는 다음과 같은 도구 API를 사용할 것입니다:

1. `where_cat_is_hiding`: 고양이가 숨어있는 위치를 반환합니다.
2. `get_items`: 특정 장소에서 찾을 수 있는 물품 목록을 제공합니다.

이러한 도구를 통해 고양이가 숨어있는 곳에 어떤 물품이 있는지 등의 질문에 답변할 수 있는 더 흥미로운 상황에서 스트리밍을 탐색할 수 있습니다.

준비되셨나요?🏎️

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_openai_tools_agent
from langchain.tools import tool
from langchain_core.callbacks import Callbacks
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
```

## 모델 생성

**주의** LLM에 `streaming=True`를 설정했습니다. 이를 통해 `astream_events` API를 사용하여 에이전트에서 토큰을 스트리밍할 수 있습니다. 이는 LangChain의 이전 버전에 필요합니다.

```python
model = ChatOpenAI(temperature=0, streaming=True)
```

## 도구

채팅 모델을 기반으로 출력을 생성하는 두 개의 도구를 정의했습니다!

```python
import random


@tool
async def where_cat_is_hiding() -> str:
    """Where is the cat hiding right now?"""
    return random.choice(["under the bed", "on the shelf"])


@tool
async def get_items(place: str) -> str:
    """Use this tool to look up which items are in the given place."""
    if "bed" in place:  # For under the bed
        return "socks, shoes and dust bunnies"
    if "shelf" in place:  # For 'shelf'
        return "books, penciles and pictures"
    else:  # if the agent decides to ask about a different place
        return "cat snacks"
```

```python
await where_cat_is_hiding.ainvoke({})
```

```output
'on the shelf'
```

```python
await get_items.ainvoke({"place": "shelf"})
```

```output
'books, penciles and pictures'
```

## 에이전트 초기화

여기서는 OpenAI 도구 에이전트를 초기화할 것입니다.

**주의** `"run_name"="Agent"`를 사용하여 우리의 에이전트에 `Agent`라는 이름을 지정했습니다. 이 사실은 나중에 `astream_events` API와 함께 사용할 것입니다.

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/openai-tools-agent")
# print(prompt.messages) 

*[truncated — see source for full prompt]*