# Tool Calling

> [ツールの呼び出し](/docs/modules/model_io/chat/function_calling)により、モデルはいつ1つ以上のツールを呼び出す必要があるかを検出し、それらのツールに渡すべき入力を返すことができます。APIコールでは、ツールを記述し、それらのツールを呼び出すための引数を

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ツールの呼び出しエージェント

[ツールの呼び出し](/docs/modules/model_io/chat/function_calling)により、モデルはいつ1つ以上のツールを呼び出す必要があるかを検出し、それらのツールに渡すべき入力を返すことができます。APIコールでは、ツールを記述し、それらのツールを呼び出すための引数を含む構造化オブジェクト(例えばJSON)を出力するようにモデルに指示することができます。ツールAPIの目的は、一般的なテキスト補完やチャットAPIを使用するよりも、信頼性の高い有効なツールの呼び出しを返すことです。

この構造化された出力を活用し、[ツールの呼び出しチャットモデル](/docs/integrations/chat/)に複数のツールをバインドして、クエリを解決するまでツールを繰り返し呼び出し、結果を受け取ることができます。

これは、OpenAIのツールエージェント(/docs/modules/agents/agent_types/openai_tools/)の一般化されたバージョンです。OpenAIの特定のツールの呼び出しスタイルに合わせて設計されていましたが、LangChainのToolCallインターフェースを使用することで、[Anthropic](/docs/integrations/chat/anthropic/)、[Google Gemini](/docs/integrations/chat/google_vertex_ai_palm/)、[Mistral](/docs/integrations/chat/mistralai/)などの幅広いプロバイダ実装をサポートできるようになりました。

## セットアップ

ツールの呼び出しをサポートするモデルであれば、このエージェントで使用できます。どのモデルがツールの呼び出しをサポートしているかは、[こちら](/docs/integrations/chat/)で確認できます。

このデモでは[Tavily](https://app.tavily.com)を使用しますが、他の[組み込みツール](/docs/integrations/tools)に置き換えたり、[カスタムツール](/docs/modules/tools/custom_tools/)を追加したりすることもできます。
APIキーの取得と`process.env.TAVILY_API_KEY`への設定が必要です。

import ChatModelTabs from "@theme/ChatModelTabs";

<ChatModelTabs
  customVarName="llm"
  hideCohere
/>

```python
# | output: false
# | echo: false

from langchain_anthropic import ChatAnthropic

llm = ChatAnthropic(model="claude-3-sonnet-20240229", temperature=0)
```

## ツールの初期化

まずは、Webを検索するツールを作成します:

```python
from langchain.agents import AgentExecutor, create_tool_calling_agent
from langchain_community.tools.tavily_search import TavilySearchResults
from langchain_core.prompts import ChatPromptTemplate

tools = [TavilySearchResults(max_results=1)]
```

## エージェントの作成

次に、ツールの呼び出しエージェントを初期化しましょう:

```python
prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are a helpful assistant. Make sure to use the tavily_search_results_json tool for information.",
        ),
        ("placeholder", "{chat_history}"),
        ("human", "{input}"),
        ("placeholder", "{agent_scratchpad}"),
    

*[truncated — see source for full prompt]*