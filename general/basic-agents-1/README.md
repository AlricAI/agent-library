# Basic Agents

> 基本的なエージェントは、ほとんどの一般的なユースケースで機能する、シンプルな実行フローを持つ定義済みのストラテジーを使用します。
これは文字列の入力（質問、リクエスト、またはタスクの説明）を受け取り、この入力を構成されたLLMに送信します。
LLMは、提供されたツールを呼び出すかどうかを決定します。

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 基本的なエージェント

基本的なエージェントは、ほとんどの一般的なユースケースで機能する、シンプルな実行フローを持つ定義済みのストラテジーを使用します。
これは文字列の入力（質問、リクエスト、またはタスクの説明）を受け取り、この入力を構成されたLLMに送信します。
LLMは、提供されたツールを呼び出すかどうかを決定します。
エージェントはツールを実行し、その結果をLLMに送り返します。
これは、LLMがそれ以上のツール呼び出しを要求しなくなり、文字列のレスポンスを返すまで繰り返されます。
その後、エージェントはそのレスポンスを出力します。

[グラフベースのエージェント](graph-based-agents.md)では、基本的なエージェントで使用されている定義済みのストラテジーグラフをどのように再作成できるかを確認できます。

??? note "前提条件"

    --8<-- "quickstart-snippets.md:prerequisites"

    --8<-- "quickstart-snippets.md:dependencies"

    --8<-- "quickstart-snippets.md:api-key"

    このページの例では、`OPENAI_API_KEY` 環境変数が設定されていることを前提としています。

## 最小限のエージェントを作成する

最も基本的なエージェントを作成するには、[`AIAgent`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent/index.html) をインスタンス化し、[言語モデル](../model-capabilities.md#creating-a-model-llmodel-configuration)を備えた [プロンプトエグゼキューター](../prompts/prompt-executors.md) を提供します。

=== "Kotlin"

    <!--- INCLUDE
    import ai.koog.agents.core.agent.AIAgent
    import ai.koog.prompt.executor.clients.openai.OpenAIModels
    import ai.koog.prompt.executor.llms.all.simpleOpenAIExecutor
    import kotlinx.coroutines.runBlocking
    -->
    ```kotlin
    val agent = AIAgent(
        promptExecutor = simpleOpenAIExecutor(System.getenv("OPENAI_API_KEY")),
        llmModel = OpenAIModels.Chat.GPT4o
    )
    ```

    このエージェントは入力を文字列として期待し、出力を文字列として返します。
    エージェントを実行するには、ユーザー入力を指定して `run()` 関数を使用します。

    ```kotlin
    fun main() = runBlocking {
        val result = agent.run("Hello! How can you help me?")
        println(result)
    }
    ```
    <!--- KNIT example-basic-01.kt -->

=== "Java"

    <!--- INCLUDE
    import ai.koog.agents.core.agent.AIAgent;
    import ai.koog.prompt.executor.clients.openai.OpenAIModels;
    import static ai.koog.prompt.executor.llms.all.SimplePromptExecutorsKt.simpleOpenAIExecutor;
    class exampleBasicJava01 {
        public static void main(String[] args) {
    -->
    <!--- SUFFIX
        }
    }
    -->
    ```java
    AIAgent<String, String> agent = AIA

*[truncated — see source for full prompt]*