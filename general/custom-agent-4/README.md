# Custom Agent

> このノートブックでは、独自のカスタムエージェントを作成する方法について説明します。

この例では、OpenAI Tool Callingを使ってこのエージェントを作成します。
**これが最も信頼できる方法です。**

最初はメモリなしで作成しますが、その後メモリを追加する方法も示します。
会話を可能

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
from langchain.agents.output_parsers.openai_to

*[truncated — see source for full prompt]*