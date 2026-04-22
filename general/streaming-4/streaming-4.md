---
name: Streaming
description: LLMアプリのUXを考える上で、ストリーミングは重要な要素です。エージェントの場合、ストリーミングはさらに複雑になります。最終的な回答のトークンだけでなく、エージェントが行う中間ステップもストリーミングしたい場合があるためです。

このノートブックでは、ストリーミングのための`stream/astr
model: claude-sonnet-4-5
---
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
tools = [get_items, where_cat_is_hiding]
agent = create_openai_tools_agent(
    model.with_config({"tags": ["agent_llm"]}), tools, prompt
)
agent_executor = AgentExecutor(agent=agent, tools=tools).with_config(
    {"run_name": "Agent"}
)
```

## 中間ステップのストリーミング

AgentExecutorの`.stream`メソッドを使ってエージェントの中間ステップをストリーミングします。

`.stream`の出力は、(action, observation)ペアが交互に出力され、最終的にエージェントが目的を達成した場合は回答が出力されます。

出力の内容は以下のようにまとめられます:

| 出力             | 内容                                                                                          |
|----------------------|------------------------------------------------------------------------------------------------------|
| **Actions**   |  `actions` `AgentAction`またはサブクラス、アクション呼び出しに対応するチャットメッセージ `messages` |
| **Observations** |  `steps` これまでのエージェントの行動履歴(現在のアクションと観察結果を含む)、`messages` 関数呼び出し結果(観察結果)のチャットメッセージ |
| **Final answer** | `output` `AgentFinish`、最終的な出力のチャットメッセージ `messages` |

```python
# Note: We use `pprint` to print only to depth 1, it makes it easier to see the output from a high level, before digging in.
import pprint

chunks = []

async for chunk in agent_executor.astream(
    {"input": "what's items are located where the cat is hiding?"}
):
    chunks.append(chunk)
    print("------")
    pprint.pprint(chunk, depth=1)
```

```output
------
{'actions': [...], 'messages': [...]}
------
{'messages': [...], 'steps': [...]}
------
{'actions': [...], 'messages': [...]}
------
{'messages': [...], 'steps': [...]}
------
{'messages': [...],
 'output': 'The items located where the cat is hiding on the shelf are books, '
           'pencils, and pictures.'}
```

### メッセージの使用

出力から基になるメッセージにアクセスできます。チャットアプリケーションで作業する際、すべてがメッセージであるため便利です。

```python
chunks[0]["actions"]
```

```output
[OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pKy4OLcBx6pR6k3GHBOlH68r', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_pKy4OLcBx6pR6k3GHBOlH68r')]
```

```python
for chunk in chunks:
    print(chunk["messages"])
```

```output
[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pKy4OLcBx6pR6k3GHBOlH68r', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})]
[FunctionMessage(content='on the shelf', name='where_cat_is_hiding')]
[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_qZTz1mRfCCXT18SUy0E07eS4', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]})]
[FunctionMessage(content='books, penciles and pictures', name='get_items')]
[AIMessage(content='The items located where the cat is hiding on the shelf are books, pencils, and pictures.')]
```

また、`actions`と`steps`に完全なログ情報が含まれているため、レンダリングの目的で処理しやすい場合があります。

### AgentAction/Observationの使用

出力にはさらに構造化された情報が`actions`と`steps`に含まれています。状況によっては便利ですが、解析が難しい場合もあります。

**注意** `AgentFinish`は`streaming`メソッドの一部として利用できません。これが必要な場合は、githubでディスカッションを開始し、その理由を説明してください。

```python
async for chunk in agent_executor.astream(
    {"input": "what's items are located where the cat is hiding?"}
):
    # Agent Action
    if "actions" in chunk:
        for action in chunk["actions"]:
            print(f"Calling Tool: `{action.tool}` with input `{action.tool_input}`")
    # Observation
    elif "steps" in chunk:
        for step in chunk["steps"]:
            print(f"Tool Result: `{step.observation}`")
    # Final result
    elif "output" in chunk:
        print(f'Final Output: {chunk["output"]}')
    else:
        raise ValueError()
    print("---")
```

```output
Calling Tool: `where_cat_is_hiding` with input `{}`
---
Tool Result: `on the shelf`
---
Calling Tool: `get_items` with input `{'place': 'shelf'}`
---
Tool Result: `books, penciles and pictures`
---
Final Output: The items located where the cat is hiding on the shelf are books, pencils, and pictures.
---
```

## カスタムストリーミングWithEvents

デフォルトの*stream*の動作が自分のアプリケーションに合わない場合(例えば、エージェントからの個々のトークンをストリーミングしたり、ツール内で発生するステップを表示したい場合)は、`astream_events` APIを使用します。

⚠️ これは**ベータ**APIであり、使用状況に応じて将来的に若干の詳細が変更される可能性があります。
⚠️ すべてのコールバックが正しく動作するようにするには、コード全体で`async`を使用してください。同期バージョンのコード(ツールの同期バージョンなど)を混在させないでください。

このAPIを使って、以下のイベントをストリーミングしましょう:

1. 入力付きのエージェント開始
1. 入力付きのツール開始
1. 出力付きのツール終了
1. エージェントの最終回答をトークンごとにストリーミング
1. 出力付きのエージェント終了

```python
async for event in agent_executor.astream_events(
    {"input": "where is the cat hiding? what items are in that location?"},
    version="v1",
):
    kind = event["event"]
    if kind == "on_chain_start":
        if (
            event["name"] == "Agent"
        ):  # Was assigned when creating the agent with `.with_config({"run_name": "Agent"})`
            print(
                f"Starting agent: {event['name']} with input: {event['data'].get('input')}"
            )
    elif kind == "on_chain_end":
        if (
            event["name"] == "Agent"
        ):  # Was assigned when creating the agent with `.with_config({"run_name": "Agent"})`
            print()
            print("--")
            print(
                f"Done agent: {event['name']} with output: {event['data'].get('output')['output']}"
            )
    if kind == "on_chat_model_stream":
        content = event["data"]["chunk"].content
        if content:
            # Empty content in the context of OpenAI means
            # that the model is asking for a tool to be invoked.
            # So we only print non-empty content
            print(content, end="|")
    elif kind == "on_tool_start":
        print("--")
        print(
            f"Starting tool: {event['name']} with inputs: {event['data'].get('input')}"
        )
    elif kind == "on_tool_end":
        print(f"Done tool: {event['name']}")
        print(f"Tool output was: {event['data'].get('output')}")
        print("--")
```

```output
Starting agent: Agent with input: {'input': 'where is the cat hiding? what items are in that location?'}
--
Starting tool: where_cat_is_hiding with inputs: {}
Done tool: where_cat_is_hiding
Tool output was: on the shelf
--
--
Starting tool: get_items with inputs: {'place': 'shelf'}
Done tool: get_items
Tool output was: books, penciles and pictures
--
The| cat| is| currently| hiding| on| the| shelf|.| In| that| location|,| you| can| find| books|,| pencils|,| and| pictures|.|
--
Done agent: Agent with output: The cat is currently hiding on the shelf. In that location, you can find books, pencils, and pictures.
```

### ツール内からのストリームイベント

ツールがLangChainの実行可能オブジェクト(LCEL chains、LLM、retrieverなど)を活用している場合、それらのオブジェクトからもイベントをストリーミングしたい場合があります。その場合、コールバックが正しく伝播されるようにする必要があります。

コールバックの渡し方を確認するため、`get_items`ツールを再実装し、LLMを使うように変更し、そのLLMにコールバックを渡します。自分のユースケースに合わせて適応してください。

```python
@tool
async def get_items(place: str, callbacks: Callbacks) -> str:  # <--- Accept callbacks
    """Use this tool to look up which items are in the given place."""
    template = ChatPromptTemplate.from_messages(
        [
            (
                "human",
                "Can you tell me what kind of items i might find in the following place: '{place}'. "
                "List at least 3 such items separating them by a comma. And include a brief description of each item..",
            )
        ]
    )
    chain = template | model.with_config(
        {
            "run_name": "Get Items LLM",
            "tags": ["tool_llm"],
            "callbacks": callbacks,  # <-- Propagate callbacks
        }
    )
    chunks = [chunk async for chunk in chain.astream({"place": place})]
    return "".join(chunk.content for chunk in chunks)
```

^ ツールがどのようにコールバックを伝播しているかを確認してください。

次に、エージェントを初期化し、新しい出力を確認しましょう。

```python
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/openai-tools-agent")
# print(prompt.messages) -- to see the prompt
tools = [get_items, where_cat_is_hiding]
agent = create_openai_tools_agent(
    model.with_config({"tags": ["agent_llm"]}), tools, prompt
)
agent_executor = AgentExecutor(agent=agent, tools=tools).with_config(
    {"run_name": "Agent"}
)

async for event in agent_executor.astream_events(
    {"input": "where is the cat hiding? what items are in that location?"},
    version="v1",
):
    kind = event["event"]
    if kind == "on_chain_start":
        if (
            event["name"] == "Agent"
        ):  # Was assigned when creating the agent with `.with_config({"run_name": "Agent"})`
            print(
                f"Starting agent: {event['name']} with input: {event['data'].get('input')}"
            )
    elif kind == "on_chain_end":
        if (
            event["name"] == "Agent"
        ):  # Was assigned when creating the agent with `.with_config({"run_name": "Agent"})`
            print()
            print("--")
            print(
                f"Done agent: {event['name']} with output: {event['data'].get('output')['output']}"
            )
    if kind == "on_chat_model_stream":
        content = event["data"]["chunk"].content
        if content:
            # Empty content in the context of OpenAI means
            # that the model is asking for a tool to be invoked.
            # So we only print non-empty content
            print(content, end="|")
    elif kind == "on_tool_start":
        print("--")
        print(
            f"Starting tool: {event['name']} with inputs: {event['data'].get('input')}"
        )
    elif kind == "on_tool_end":
        print(f"Done tool: {event['name']}")
        print(f"Tool output was: {event['data'].get('output')}")
        print("--")
```

```output
Starting agent: Agent with input: {'input': 'where is the cat hiding? what items are in that location?'}
--
Starting tool: where_cat_is_hiding with inputs: {}
Done tool: where_cat_is_hiding
Tool output was: on the shelf
--
--
Starting tool: get_items with inputs: {'place': 'shelf'}
In| a| shelf|,| you| might| find|:

|1|.| Books|:| A| shelf| is| commonly| used| to| store| books|.| It| may| contain| various| genres| such| as| novels|,| textbooks|,| or| reference| books|.| Books| provide| knowledge|,| entertainment|,| and| can| transport| you| to| different| worlds| through| storytelling|.

|2|.| Decor|ative| items|:| Sh|elves| often| display| decorative| items| like| figur|ines|,| v|ases|,| or| photo| frames|.| These| items| add| a| personal| touch| to| the| space| and| can| reflect| the| owner|'s| interests| or| memories|.

|3|.| Storage| boxes|:| Sh|elves| can| also| hold| storage| boxes| or| baskets|.| These| containers| help| organize| and| decl|utter| the| space| by| storing| miscellaneous| items| like| documents|,| accessories|,| or| small| household| items|.| They| provide| a| neat| and| tidy| appearance| to| the| shelf|.|Done tool: get_items
Tool output was: In a shelf, you might find:

1. Books: A shelf is commonly used to store books. It may contain various genres such as novels, textbooks, or reference books. Books provide knowledge, entertainment, and can transport you to different worlds through storytelling.

2. Decorative items: Shelves often display decorative items like figurines, vases, or photo frames. These items add a personal touch to the space and can reflect the owner's interests or memories.

3. Storage boxes: Shelves can also hold storage boxes or baskets. These containers help organize and declutter the space by storing miscellaneous items like documents, accessories, or small household items. They provide a neat and tidy appearance to the shelf.
--
The| cat| is| hiding| on| the| shelf|.| In| that| location|,| you| might| find| books|,| decorative| items|,| and| storage| boxes|.|
--
Done agent: Agent with output: The cat is hiding on the shelf. In that location, you might find books, decorative items, and storage boxes.
```

### その他のアプローチ

#### astream_logの使用

**注意** [astream_log](/docs/expression_language/interface#async-stream-intermediate-steps) APIも使用できます。このAPIは、実行中に発生するすべてのイベントの詳細なログを生成します。ログ形式は[JSONPatch](https://jsonpatch.com/)標準に基づいています。詳細ですが、解析するのに手間がかかります。そのため、`astream_events` APIを作成しました。

```python
i = 0
async for chunk in agent_executor.astream_log(
    {"input": "where is the cat hiding? what items are in that location?"},
):
    print(chunk)
    i += 1
    if i > 10:
        break
```

```output
RunLogPatch({'op': 'replace',
  'path': '',
  'value': {'final_output': None,
            'id': 'c261bc30-60d1-4420-9c66-c6c0797f2c2d',
            'logs': {},
            'name': 'Agent',
            'streamed_output': [],
            'type': 'chain'}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableSequence',
  'value': {'end_time': None,
            'final_output': None,
            'id': '183cb6f8-ed29-4967-b1ea-024050ce66c7',
            'metadata': {},
            'name': 'RunnableSequence',
            'start_time': '2024-01-22T20:38:43.650+00:00',
            'streamed_output': [],
            'streamed_output_str': [],
            'tags': [],
            'type': 'chain'}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableAssign<agent_scratchpad>',
  'value': {'end_time': None,
            'final_output': None,
            'id': '7fe1bb27-3daf-492e-bc7e-28602398f008',
            'metadata': {},
            'name': 'RunnableAssign<agent_scratchpad>',
            'start_time': '2024-01-22T20:38:43.652+00:00',
            'streamed_output': [],
            'streamed_output_str': [],
            'tags': ['seq:step:1'],
            'type': 'chain'}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableAssign<agent_scratchpad>/streamed_output/-',
  'value': {'input': 'where is the cat hiding? what items are in that '
                     'location?',
            'intermediate_steps': []}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableParallel<agent_scratchpad>',
  'value': {'end_time': None,
            'final_output': None,
            'id': 'b034e867-e6bb-4296-bfe6-752c44fba6ce',
            'metadata': {},
            'name': 'RunnableParallel<agent_scratchpad>',
            'start_time': '2024-01-22T20:38:43.652+00:00',
            'streamed_output': [],
            'streamed_output_str': [],
            'tags': [],
            'type': 'chain'}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableLambda',
  'value': {'end_time': None,
            'final_output': None,
            'id': '65ceef3e-7a80-4015-8b5b-d949326872e9',
            'metadata': {},
            'name': 'RunnableLambda',
            'start_time': '2024-01-22T20:38:43.653+00:00',
            'streamed_output': [],
            'streamed_output_str': [],
            'tags': ['map:key:agent_scratchpad'],
            'type': 'chain'}})
RunLogPatch({'op': 'add', 'path': '/logs/RunnableLambda/streamed_output/-', 'value': []})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableParallel<agent_scratchpad>/streamed_output/-',
  'value': {'agent_scratchpad': []}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableAssign<agent_scratchpad>/streamed_output/-',
  'value': {'agent_scratchpad': []}})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableLambda/final_output',
  'value': {'output': []}},
 {'op': 'add',
  'path': '/logs/RunnableLambda/end_time',
  'value': '2024-01-22T20:38:43.654+00:00'})
RunLogPatch({'op': 'add',
  'path': '/logs/RunnableParallel<agent_scratchpad>/final_output',
  'value': {'agent_scratchpad': []}},
 {'op': 'add',
  'path': '/logs/RunnableParallel<agent_scratchpad>/end_time',
  'value': '2024-01-22T20:38:43.655+00:00'})
```

これを使いやすい形式で取得するには、ある程度のロジックが必要かもしれません。

```python
i = 0
path_status = {}
async for chunk in agent_executor.astream_log(
    {"input": "where is the cat hiding? what items are in that location?"},
):
    for op in chunk.ops:
        if op["op"] == "add":
            if op["path"] not in path_status:
                path_status[op["path"]] = op["value"]
            else:
                path_status[op["path"]] += op["value"]
    print(op["path"])
    print(path_status.get(op["path"]))
    print("----")
    i += 1
    if i > 30:
        break
```

```output

None
----
/logs/RunnableSequence
{'id': '22bbd5db-9578-4e3f-a6ec-9b61f08cb8a9', 'name': 'RunnableSequence', 'type': 'chain', 'tags': [], 'metadata': {}, 'start_time': '2024-01-22T20:38:43.668+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/RunnableAssign<agent_scratchpad>
{'id': 'e0c00ae2-aaa2-4a09-bc93-cb34bf3f6554', 'name': 'RunnableAssign<agent_scratchpad>', 'type': 'chain', 'tags': ['seq:step:1'], 'metadata': {}, 'start_time': '2024-01-22T20:38:43.672+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/RunnableAssign<agent_scratchpad>/streamed_output/-
{'input': 'where is the cat hiding? what items are in that location?', 'intermediate_steps': []}
----
/logs/RunnableParallel<agent_scratchpad>
{'id': '26ff576d-ff9d-4dea-98b2-943312a37f4d', 'name': 'RunnableParallel<agent_scratchpad>', 'type': 'chain', 'tags': [], 'metadata': {}, 'start_time': '2024-01-22T20:38:43.674+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/RunnableLambda
{'id': '9f343c6a-23f7-4a28-832f-d4fe3e95d1dc', 'name': 'RunnableLambda', 'type': 'chain', 'tags': ['map:key:agent_scratchpad'], 'metadata': {}, 'start_time': '2024-01-22T20:38:43.685+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/RunnableLambda/streamed_output/-
[]
----
/logs/RunnableParallel<agent_scratchpad>/streamed_output/-
{'agent_scratchpad': []}
----
/logs/RunnableAssign<agent_scratchpad>/streamed_output/-
{'input': 'where is the cat hiding? what items are in that location?', 'intermediate_steps': [], 'agent_scratchpad': []}
----
/logs/RunnableLambda/end_time
2024-01-22T20:38:43.687+00:00
----
/logs/RunnableParallel<agent_scratchpad>/end_time
2024-01-22T20:38:43.688+00:00
----
/logs/RunnableAssign<agent_scratchpad>/end_time
2024-01-22T20:38:43.688+00:00
----
/logs/ChatPromptTemplate
{'id': '7e3a84d5-46b8-4782-8eed-d1fe92be6a30', 'name': 'ChatPromptTemplate', 'type': 'prompt', 'tags': ['seq:step:2'], 'metadata': {}, 'start_time': '2024-01-22T20:38:43.689+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/ChatPromptTemplate/end_time
2024-01-22T20:38:43.689+00:00
----
/logs/ChatOpenAI
{'id': '6446f7ec-b3e4-4637-89d8-b4b34b46ea14', 'name': 'ChatOpenAI', 'type': 'llm', 'tags': ['seq:step:3', 'agent_llm'], 'metadata': {}, 'start_time': '2024-01-22T20:38:43.690+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/ChatOpenAI/streamed_output/-
content='' additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_gKFg6FX8ZQ88wFUs94yx86PF', 'function': {'arguments': '', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}
----
/logs/ChatOpenAI/streamed_output/-
content='' additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_gKFg6FX8ZQ88wFUs94yx86PF', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}
----
/logs/ChatOpenAI/streamed_output/-
content='' additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_gKFg6FX8ZQ88wFUs94yx86PF', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}
----
/logs/ChatOpenAI/end_time
2024-01-22T20:38:44.203+00:00
----
/logs/OpenAIToolsAgentOutputParser
{'id': '65912835-8dcd-4be2-ad05-9f239a7ef704', 'name': 'OpenAIToolsAgentOutputParser', 'type': 'parser', 'tags': ['seq:step:4'], 'metadata': {}, 'start_time': '2024-01-22T20:38:44.204+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/OpenAIToolsAgentOutputParser/end_time
2024-01-22T20:38:44.205+00:00
----
/logs/RunnableSequence/streamed_output/-
[OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_gKFg6FX8ZQ88wFUs94yx86PF', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_gKFg6FX8ZQ88wFUs94yx86PF')]
----
/logs/RunnableSequence/end_time
2024-01-22T20:38:44.206+00:00
----
/final_output
None
----
/logs/where_cat_is_hiding
{'id': '21fde139-0dfa-42bb-ad90-b5b1e984aaba', 'name': 'where_cat_is_hiding', 'type': 'tool', 'tags': [], 'metadata': {}, 'start_time': '2024-01-22T20:38:44.208+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/where_cat_is_hiding/end_time
2024-01-22T20:38:44.208+00:00
----
/final_output/messages/1
content='under the bed' name='where_cat_is_hiding'
----
/logs/RunnableSequence:2
{'id': '37d52845-b689-4c18-9c10-ffdd0c4054b0', 'name': 'RunnableSequence', 'type': 'chain', 'tags': [], 'metadata': {}, 'start_time': '2024-01-22T20:38:44.210+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/RunnableAssign<agent_scratchpad>:2
{'id': '30024dea-064f-4b04-b130-671f47ac59bc', 'name': 'RunnableAssign<agent_scratchpad>', 'type': 'chain', 'tags': ['seq:step:1'], 'metadata': {}, 'start_time': '2024-01-22T20:38:44.213+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
/logs/RunnableAssign<agent_scratchpad>:2/streamed_output/-
{'input': 'where is the cat hiding? what items are in that location?', 'intermediate_steps': [(OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_gKFg6FX8ZQ88wFUs94yx86PF', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_gKFg6FX8ZQ88wFUs94yx86PF'), 'under the bed')]}
----
/logs/RunnableParallel<agent_scratchpad>:2
{'id': '98906cd7-93c2-47e8-a7d7-2e8d4ab09ed0', 'name': 'RunnableParallel<agent_scratchpad>', 'type': 'chain', 'tags': [], 'metadata': {}, 'start_time': '2024-01-22T20:38:44.215+00:00', 'streamed_output': [], 'streamed_output_str': [], 'final_output': None, 'end_time': None}
----
```

#### コールバックの使用(レガシー)

ストリーミングにもう一つのアプローチとして、コールバックを使用する方法があります。これは、LangChainの古いバージョンを使用しており、アップグレードできない場合に役立つかもしれません。

一般的に、これは**推奨されるアプローチではありません**。なぜなら:

1. ほとんどのアプリケーションでは、2つのワーカーを作成し、コールバックをキューに書き込み、別のワーカーがキューから読み取る必要があります(つまり、これを機能させるには隠れた複雑さがあります)。
2. **end**イベントには、実行名などのメタデータが欠落している可能性があります。したがって、関連情報を取得したい場合は、`AsyncCallbackHandler`ではなく`BaseTracer`を継承する必要があるか、`run_id`に基づいて集計ロジックを自分で実装する必要があります。
3. コールバックの動作は一貫していません(入力と出力のエンコーディングなど)。これらの違いに対処する必要があります。

説明のために、トークンごとのストリーミングを取得するためのコールバックの実装例を示します。アプリケーションのニーズに応じて、他のコールバックを実装することもできます。

ただし、`astream_events`はこれらすべてを内部で処理するので、自分で実装する必要はありません。

```python
from typing import TYPE_CHECKING, Any, Dict, List, Optional, Sequence, TypeVar, Union
from uuid import UUID

from langchain_core.callbacks.base import AsyncCallbackHandler
from langchain_core.messages import BaseMessage
from langchain_core.outputs import ChatGenerationChunk, GenerationChunk, LLMResult

# Here is a custom handler that will print the tokens to stdout.
# Instead of printing to stdout you can send the data elsewhere; e.g., to a streaming API response


class TokenByTokenHandler(AsyncCallbackHandler):
    def __init__(self, tags_of_interest: List[str]) -> None:
        """A custom call back handler.

        Args:
            tags_of_interest: Only LLM tokens from models with these tags will be
                              printed.
        """
        self.tags_of_interest = tags_of_interest

    async def on_chain_start(
        self,
        serialized: Dict[str, Any],
        inputs: Dict[str, Any],
        *,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        tags: Optional[List[str]] = None,
        metadata: Optional[Dict[str, Any]] = None,
        **kwargs: Any,
    ) -> None:
        """Run when chain starts running."""
        print("on chain start: ")
        print(inputs)

    async def on_chain_end(
        self,
        outputs: Dict[str, Any],
        *,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        tags: Optional[List[str]] = None,
        **kwargs: Any,
    ) -> None:
        """Run when chain ends running."""
        print("On chain end")
        print(outputs)

    async def on_chat_model_start(
        self,
        serialized: Dict[str, Any],
        messages: List[List[BaseMessage]],
        *,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        tags: Optional[List[str]] = None,
        metadata: Optional[Dict[str, Any]] = None,
        **kwargs: Any,
    ) -> Any:
        """Run when a chat model starts running."""
        overlap_tags = self.get_overlap_tags(tags)

        if overlap_tags:
            print(",".join(overlap_tags), end=": ", flush=True)

    def on_tool_start(
        self,
        serialized: Dict[str, Any],
        input_str: str,
        *,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        tags: Optional[List[str]] = None,
        metadata: Optional[Dict[str, Any]] = None,
        inputs: Optional[Dict[str, Any]] = None,
        **kwargs: Any,
    ) -> Any:
        """Run when tool starts running."""
        print("Tool start")
        print(serialized)

    def on_tool_end(
        self,
        output: Any,
        *,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        **kwargs: Any,
    ) -> Any:
        """Run when tool ends running."""
        print("Tool end")
        print(str(output))

    async def on_llm_end(
        self,
        response: LLMResult,
        *,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        tags: Optional[List[str]] = None,
        **kwargs: Any,
    ) -> None:
        """Run when LLM ends running."""
        overlap_tags = self.get_overlap_tags(tags)

        if overlap_tags:
            # Who can argue with beauty?
            print()
            print()

    def get_overlap_tags(self, tags: Optional[List[str]]) -> List[str]:
        """Check for overlap with filtered tags."""
        if not tags:
            return []
        return sorted(set(tags or []) & set(self.tags_of_interest or []))

    async def on_llm_new_token(
        self,
        token: str,
        *,
        chunk: Optional[Union[GenerationChunk, ChatGenerationChunk]] = None,
        run_id: UUID,
        parent_run_id: Optional[UUID] = None,
        tags: Optional[List[str]] = None,
        **kwargs: Any,
    ) -> None:
        """Run on new LLM token. Only available when streaming is enabled."""
        overlap_tags = self.get_overlap_tags(tags)

        if token and overlap_tags:
            print(token, end="|", flush=True)


handler = TokenByTokenHandler(tags_of_interest=["tool_llm", "agent_llm"])

result = await agent_executor.ainvoke(
    {"input": "where is the cat hiding and what items can be found there?"},
    {"callbacks": [handler]},
)
```

```output
on chain start:
{'input': 'where is the cat hiding and what items can be found there?'}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
On chain end
[]
On chain end
{'agent_scratchpad': []}
On chain end
{'input': 'where is the cat hiding and what items can be found there?', 'intermediate_steps': [], 'agent_scratchpad': []}
on chain start:
{'input': 'where is the cat hiding and what items can be found there?', 'intermediate_steps': [], 'agent_scratchpad': []}
On chain end
{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'prompts', 'chat', 'ChatPromptValue'], 'kwargs': {'messages': [{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'SystemMessage'], 'kwargs': {'content': 'You are a helpful assistant', 'additional_kwargs': {}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'HumanMessage'], 'kwargs': {'content': 'where is the cat hiding and what items can be found there?', 'additional_kwargs': {}}}]}}
agent_llm:

on chain start:
content='' additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}
On chain end
[{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'agent', 'OpenAIToolAgentAction'], 'kwargs': {'tool': 'where_cat_is_hiding', 'tool_input': {}, 'log': '\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', 'message_log': [{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'AIMessageChunk'], 'kwargs': {'example': False, 'content': '', 'additional_kwargs': {'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}}}], 'tool_call_id': 'call_pboyZTT0587rJtujUluO2OOc'}}]
On chain end
[OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_pboyZTT0587rJtujUluO2OOc')]
Tool start
{'name': 'where_cat_is_hiding', 'description': 'where_cat_is_hiding() -> str - Where is the cat hiding right now?'}
Tool end
on the shelf
on chain start:
{'input': ''}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
On chain end
[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc')]
On chain end
{'agent_scratchpad': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc')]}
On chain end
{'input': 'where is the cat hiding and what items can be found there?', 'intermediate_steps': [(OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), 'on the shelf')], 'agent_scratchpad': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc')]}
on chain start:
{'input': 'where is the cat hiding and what items can be found there?', 'intermediate_steps': [(OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), 'on the shelf')], 'agent_scratchpad': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc')]}
On chain end
{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'prompts', 'chat', 'ChatPromptValue'], 'kwargs': {'messages': [{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'SystemMessage'], 'kwargs': {'content': 'You are a helpful assistant', 'additional_kwargs': {}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'HumanMessage'], 'kwargs': {'content': 'where is the cat hiding and what items can be found there?', 'additional_kwargs': {}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'AIMessageChunk'], 'kwargs': {'example': False, 'content': '', 'additional_kwargs': {'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'ToolMessage'], 'kwargs': {'tool_call_id': 'call_pboyZTT0587rJtujUluO2OOc', 'content': 'on the shelf', 'additional_kwargs': {'name': 'where_cat_is_hiding'}}}]}}
agent_llm:

on chain start:
content='' additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}
On chain end
[{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'agent', 'OpenAIToolAgentAction'], 'kwargs': {'tool': 'get_items', 'tool_input': {'place': 'shelf'}, 'log': "\nInvoking: `get_items` with `{'place': 'shelf'}`\n\n\n", 'message_log': [{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'AIMessageChunk'], 'kwargs': {'example': False, 'content': '', 'additional_kwargs': {'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}}}], 'tool_call_id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh'}}]
On chain end
[OpenAIToolAgentAction(tool='get_items', tool_input={'place': 'shelf'}, log="\nInvoking: `get_items` with `{'place': 'shelf'}`\n\n\n", message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]})], tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh')]
Tool start
{'name': 'get_items', 'description': 'get_items(place: str, callbacks: Union[List[langchain_core.callbacks.base.BaseCallbackHandler], langchain_core.callbacks.base.BaseCallbackManager, NoneType]) -> str - Use this tool to look up which items are in the given place.'}
tool_llm: In| a| shelf|,| you| might| find|:

|1|.| Books|:| A| shelf| is| commonly| used| to| store| books|.| Books| can| be| of| various| genres|,| such| as| novels|,| textbooks|,| or| reference| books|.| They| provide| knowledge|,| entertainment|,| and| can| transport| you| to| different| worlds| through| storytelling|.

|2|.| Decor|ative| items|:| Sh|elves| often| serve| as| a| display| area| for| decorative| items| like| figur|ines|,| v|ases|,| or| sculptures|.| These| items| add| aesthetic| value| to| the| space| and| reflect| the| owner|'s| personal| taste| and| style|.

|3|.| Storage| boxes|:| Sh|elves| can| also| be| used| to| store| various| items| in| organized| boxes|.| These| boxes| can| hold| anything| from| office| supplies|,| craft| materials|,| or| sentimental| items|.| They| help| keep| the| space| tidy| and| provide| easy| access| to| stored| belongings|.|

Tool end
In a shelf, you might find:

1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.

2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.

3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.
on chain start:
{'input': ''}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
on chain start:
{'input': ''}
On chain end
[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}), ToolMessage(content="In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.", additional_kwargs={'name': 'get_items'}, tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh')]
On chain end
{'agent_scratchpad': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}), ToolMessage(content="In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.", additional_kwargs={'name': 'get_items'}, tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh')]}
On chain end
{'input': 'where is the cat hiding and what items can be found there?', 'intermediate_steps': [(OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), 'on the shelf'), (OpenAIToolAgentAction(tool='get_items', tool_input={'place': 'shelf'}, log="\nInvoking: `get_items` with `{'place': 'shelf'}`\n\n\n", message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]})], tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh'), "In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.")], 'agent_scratchpad': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}), ToolMessage(content="In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.", additional_kwargs={'name': 'get_items'}, tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh')]}
on chain start:
{'input': 'where is the cat hiding and what items can be found there?', 'intermediate_steps': [(OpenAIToolAgentAction(tool='where_cat_is_hiding', tool_input={}, log='\nInvoking: `where_cat_is_hiding` with `{}`\n\n\n', message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]})], tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), 'on the shelf'), (OpenAIToolAgentAction(tool='get_items', tool_input={'place': 'shelf'}, log="\nInvoking: `get_items` with `{'place': 'shelf'}`\n\n\n", message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]})], tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh'), "In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.")], 'agent_scratchpad': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}), ToolMessage(content='on the shelf', additional_kwargs={'name': 'where_cat_is_hiding'}, tool_call_id='call_pboyZTT0587rJtujUluO2OOc'), AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}), ToolMessage(content="In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.", additional_kwargs={'name': 'get_items'}, tool_call_id='call_vIVtgUb9Gvmc3zAGIrshnmbh')]}
On chain end
{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'prompts', 'chat', 'ChatPromptValue'], 'kwargs': {'messages': [{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'SystemMessage'], 'kwargs': {'content': 'You are a helpful assistant', 'additional_kwargs': {}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'HumanMessage'], 'kwargs': {'content': 'where is the cat hiding and what items can be found there?', 'additional_kwargs': {}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'AIMessageChunk'], 'kwargs': {'example': False, 'content': '', 'additional_kwargs': {'tool_calls': [{'index': 0, 'id': 'call_pboyZTT0587rJtujUluO2OOc', 'function': {'arguments': '{}', 'name': 'where_cat_is_hiding'}, 'type': 'function'}]}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'ToolMessage'], 'kwargs': {'tool_call_id': 'call_pboyZTT0587rJtujUluO2OOc', 'content': 'on the shelf', 'additional_kwargs': {'name': 'where_cat_is_hiding'}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'AIMessageChunk'], 'kwargs': {'example': False, 'content': '', 'additional_kwargs': {'tool_calls': [{'index': 0, 'id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'function': {'arguments': '{\n  "place": "shelf"\n}', 'name': 'get_items'}, 'type': 'function'}]}}}, {'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'messages', 'ToolMessage'], 'kwargs': {'tool_call_id': 'call_vIVtgUb9Gvmc3zAGIrshnmbh', 'content': "In a shelf, you might find:\n\n1. Books: A shelf is commonly used to store books. Books can be of various genres, such as novels, textbooks, or reference books. They provide knowledge, entertainment, and can transport you to different worlds through storytelling.\n\n2. Decorative items: Shelves often serve as a display area for decorative items like figurines, vases, or sculptures. These items add aesthetic value to the space and reflect the owner's personal taste and style.\n\n3. Storage boxes: Shelves can also be used to store various items in organized boxes. These boxes can hold anything from office supplies, craft materials, or sentimental items. They help keep the space tidy and provide easy access to stored belongings.", 'additional_kwargs': {'name': 'get_items'}}}]}}
agent_llm: The| cat| is| hiding| on| the| shelf|.| In| the| shelf|,| you| might| find| books|,| decorative| items|,| and| storage| boxes|.|

on chain start:
content='The cat is hiding on the shelf. In the shelf, you might find books, decorative items, and storage boxes.'
On chain end
{'lc': 1, 'type': 'constructor', 'id': ['langchain', 'schema', 'agent', 'AgentFinish'], 'kwargs': {'return_values': {'output': 'The cat is hiding on the shelf. In the shelf, you might find books, decorative items, and storage boxes.'}, 'log': 'The cat is hiding on the shelf. In the shelf, you might find books, decorative items, and storage boxes.'}}
On chain end
return_values={'output': 'The cat is hiding on the shelf. In the shelf, you might find books, decorative items, and storage boxes.'} log='The cat is hiding on the shelf. In the shelf, you might find books, decorative items, and storage boxes.'
On chain end
{'output': 'The cat is hiding on the shelf. In the shelf, you might find books, decorative items, and storage boxes.'}
```