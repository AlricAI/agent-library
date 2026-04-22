# Streaming

> LLMアプリのUXを考える上で、ストリーミングは重要な要素です。エージェントの場合、ストリーミングはさらに複雑になります。最終的な回答のトークンだけでなく、エージェントが行う中間ステップもストリーミングしたい場合があるためです。

このノートブックでは、ストリーミングのための`stream/astr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ストリーミング

LLMアプリのUXを考える上で、ストリーミングは重要な要素です。エージェントの場合、ストリーミングはさらに複雑になります。最終的な回答のトークンだけでなく、エージェントが行う中間ステップもストリーミングしたい場合があるためです。

このノートブックでは、ストリーミングのための`stream/astream`と`astream_events`について説明します。

エージェントは以下のツールAPIを使用します:

1. `where_cat_is_hiding`: 猫が隠れている場所を返す
2. `get_items`: ある場所にある物品のリストを返す

これらのツールを使うことで、エージェントが両方のツールを使って質問に答える必要がある、より興味深い状況でストリーミングを探求できます(例: "猫が隠れている場所にある物品は何ですか?"という質問に答えるため)。

準備はいいですか?🏎️

```python
from langchain import hub
from langchain.agents import AgentExecutor, create_openai_tools_agent
from langchain.tools import tool
from langchain_core.callbacks import Callbacks
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
```

## モデルの作成

**注意** LLMの`streaming=True`を設定しています。これにより、`astream_events` APIを使ってエージェントからトークンをストリーミングできるようになります。これは、LangChainの古いバージョンで必要です。

```python
model = ChatOpenAI(temperature=0, streaming=True)
```

## ツール

チャットモデルを使って出力を生成するツールを2つ定義します!

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

## エージェントの初期化

ここでは、OpenAIツールエージェントを初期化します。

**注意** `"run_name"="Agent"`を使って、エージェントに`Agent`という名前を付けました。後ほど`astream_events` APIで使用します。

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/openai-tools-agent")
# print(prompt.messages) -- to see the prompt
tools = [get_

*[truncated — see source for full prompt]*