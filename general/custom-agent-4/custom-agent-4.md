---
name: Custom Agent
description: このノートブックでは、独自のカスタムエージェントを作成する方法について説明します。

この例では、OpenAI Tool Callingを使ってこのエージェントを作成します。
**これが最も信頼できる方法です。**

最初はメモリなしで作成しますが、その後メモリを追加する方法も示します。
会話を可能
model: claude-sonnet-4-5
---
# カスタムエージェント

このノートブックでは、独自のカスタムエージェントを作成する方法について説明します。

この例では、OpenAI Tool Callingを使ってこのエージェントを作成します。
**これが最も信頼できる方法です。**

最初はメモリなしで作成しますが、その後メモリを追加する方法も示します。
会話を可能にするにはメモリが必要です。

## LLMの読み込み

まず、エージェントを制御するために使用する言語モデルを読み込みましょう。

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo", temperature=0)
```

## ツールの定義

次に、使用するツールを定義しましょう。
単語の長さを計算する簡単なPythonの関数を書きます。

ここで使用する関数のドキュメント文字列は重要です。なぜそうなのかについては[こちら](/docs/modules/tools/custom_tools)で詳しく説明しています。

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

## プロンプトの作成

次にプロンプトを作成しましょう。
OpenAI Function Callingはツールの使用に特化しているため、推論方法や出力フォーマットについての指示はほとんど必要ありません。
入力変数は2つ、`input`と`agent_scratchpad`です。`input`にはユーザーの目的を含む文字列を、`agent_scratchpad`には過去のエージェントのツール呼び出しとその出力結果を含むシーケンスを入力します。

```python
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are very powerful assistant, but don't know current events",
        ),
        ("user", "{input}"),
        MessagesPlaceholder(variable_name="agent_scratchpad"),
    ]
)
```

## LLMにツールをバインド

エージェントはどのようにツールを使えるかを知っているのでしょうか?

この場合、ツールを別の引数として受け取るOpenAI tool calling LLMを使用しています。これらのLLMはツールの使用方法を特に訓練されています。

エージェントにツールを渡すには、[OpenAIのツール形式](https://platform.openai.com/docs/api-reference/chat/create)に合わせてフォーマットし、モデルに渡します。(関数を`bind`することで、モデルを呼び出す際にツールも渡されるようになります。)

```python
llm_with_tools = llm.bind_tools(tools)
```

## エージェントの作成

これらのパーツを組み合わせて、エージェントを作成することができます。
最後に2つのユーティリティ関数をインポートします。1つは中間ステップ(エージェントのアクション、ツールの出力)をモデルに入力できる形式に整形するためのもの、もう1つはモデルの出力をエージェントのアクションやタスク完了に変換するためのものです。

```python
from langchain.agents.format_scratchpad.openai_tools import (
    format_to_openai_tool_messages,
)
from langchain.agents.output_parsers.openai_tools import OpenAIToolsAgentOutputParser

agent = (
    {
        "input": lambda x: x["input"],
        "agent_scratchpad": lambda x: format_to_openai_tool_messages(
            x["intermediate_steps"]
        ),
    }
    | prompt
    | llm_with_tools
    | OpenAIToolsAgentOutputParser()
)
```

```python
from langchain.agents import AgentExecutor

agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

```python
list(agent_executor.stream({"input": "How many letters in the word eudca"}))
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m
Invoking: `get_word_length` with `{'word': 'eudca'}`


[0m[36;1m[1;3m5[0m[32;1m[1;3mThere are 5 letters in the word "eudca".[0m

[1m> Finished chain.[0m
```

```output
[{'actions': [OpenAIToolAgentAction(tool='get_word_length', tool_input={'word': 'eudca'}, log="\nInvoking: `get_word_length` with `{'word': 'eudca'}`\n\n\n", message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_A07D5TuyqcNIL0DIEVRPpZkg', 'function': {'arguments': '{\n  "word": "eudca"\n}', 'name': 'get_word_length'}, 'type': 'function'}]})], tool_call_id='call_A07D5TuyqcNIL0DIEVRPpZkg')],
  'messages': [AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_A07D5TuyqcNIL0DIEVRPpZkg', 'function': {'arguments': '{\n  "word": "eudca"\n}', 'name': 'get_word_length'}, 'type': 'function'}]})]},
 {'steps': [AgentStep(action=OpenAIToolAgentAction(tool='get_word_length', tool_input={'word': 'eudca'}, log="\nInvoking: `get_word_length` with `{'word': 'eudca'}`\n\n\n", message_log=[AIMessageChunk(content='', additional_kwargs={'tool_calls': [{'index': 0, 'id': 'call_A07D5TuyqcNIL0DIEVRPpZkg', 'function': {'arguments': '{\n  "word": "eudca"\n}', 'name': 'get_word_length'}, 'type': 'function'}]})], tool_call_id='call_A07D5TuyqcNIL0DIEVRPpZkg'), observation=5)],
  'messages': [FunctionMessage(content='5', name='get_word_length')]},
 {'output': 'There are 5 letters in the word "eudca".',
  'messages': [AIMessage(content='There are 5 letters in the word "eudca".')]}]
```

ベースのLLMと比較すると、LLMだけでは限界があることがわかります。

```python
llm.invoke("How many letters in the word educa")
```

```output
AIMessage(content='There are 6 letters in the word "educa".')
```

## メモリの追加

これでエージェントができました!
ただし、このエージェントは状態を持たず、過去の対話を記憶していません。
そのため、フォローアップの質問をすることができません。
メモリを追加して、この問題を解決しましょう。

メモリを追加するには、2つのことを行う必要があります。

1. プロンプトにメモリ変数の場所を追加する
2. チャット履歴を追跡する

まずは、プロンプトにメモリの場所を追加しましょう。
`"chat_history"`というキーでメッセージのプレースホルダーを追加します。
新しいユーザー入力の前に置くことに注意してください(会話の流れに合わせるため)。

```python
from langchain_core.prompts import MessagesPlaceholder

MEMORY_KEY = "chat_history"
prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are very powerful assistant, but bad at calculating lengths of words.",
        ),
        MessagesPlaceholder(variable_name=MEMORY_KEY),
        ("user", "{input}"),
        MessagesPlaceholder(variable_name="agent_scratchpad"),
    ]
)
```

次に、チャット履歴を追跡するリストを設定します。

```python
from langchain_core.messages import AIMessage, HumanMessage

chat_history = []
```

それらを組み合わせると、完成です!

```python
agent = (
    {
        "input": lambda x: x["input"],
        "agent_scratchpad": lambda x: format_to_openai_tool_messages(
            x["intermediate_steps"]
        ),
        "chat_history": lambda x: x["chat_history"],
    }
    | prompt
    | llm_with_tools
    | OpenAIToolsAgentOutputParser()
)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

実行する際は、入力と出力をチャット履歴として追跡する必要があります。

```python
input1 = "how many letters in the word educa?"
result = agent_executor.invoke({"input": input1, "chat_history": chat_history})
chat_history.extend(
    [
        HumanMessage(content=input1),
        AIMessage(content=result["output"]),
    ]
)
agent_executor.invoke({"input": "is that a real word?", "chat_history": chat_history})
```

```output


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3m
Invoking: `get_word_length` with `{'word': 'educa'}`


[0m[36;1m[1;3m5[0m[32;1m[1;3mThere are 5 letters in the word "educa".[0m

[1m> Finished chain.[0m


[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3mNo, "educa" is not a real word in English.[0m

[1m> Finished chain.[0m
```

```output
{'input': 'is that a real word?',
 'chat_history': [HumanMessage(content='how many letters in the word educa?'),
  AIMessage(content='There are 5 letters in the word "educa".')],
 'output': 'No, "educa" is not a real word in English.'}
```