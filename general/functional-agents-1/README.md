# Functional Agents

> 関数型エージェントでは、ユーザー入力の処理、LLMとのやり取り、必要に応じたツールの呼び出し、および最終的な出力の生成を行う関数としてロジックを実装します。
[グラフベースのエージェント](graph-based-agents.md)と比較すると、通常、プロトタイピングをより迅速に行うことができます

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 関数型エージェント

関数型エージェントでは、ユーザー入力の処理、LLMとのやり取り、必要に応じたツールの呼び出し、および最終的な出力の生成を行う関数としてロジックを実装します。
[グラフベースのエージェント](graph-based-agents.md)と比較すると、通常、プロトタイピングをより迅速に行うことができますが、以下のようなデメリットがあります。

- 視覚化が容易ではない
- 状態の永続化がない

??? note "前提条件"

    --8<-- "quickstart-snippets.md:prerequisites"

    --8<-- "quickstart-snippets.md:dependencies"

    --8<-- "quickstart-snippets.md:api-key"

    このページの例では、Ollamaを介してLlama 3.2をローカルで実行していることを前提としています。

このページでは、エージェントのカスタムロジックを迅速にプロトタイプするための関数型戦略の実装方法について説明します。

## 最小限の関数型エージェントを作成する

最小限の関数型エージェントを作成するには、[基本エージェント](basic-agents.md)と同じ[`AIAgent`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent/index.html)インターフェースを使用し、[`AIAgentFunctionalStrategy`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent-functional-strategy/index.html)のインスタンスを渡します。
入力を受け取り出力を返し、1回のLLM呼び出しを行い、レスポンスからアシスタントメッセージの内容を返す関数型戦略を定義できます。

Kotlinでは、`functionalStrategy {...}` DSLメソッドを使用するのが最も便利です。Javaでは、`AIAgent`ビルダーの`functionalStrategy`メソッドを使用できます。

=== "Kotlin"

    <!--- INCLUDE
    import ai.koog.agents.core.agent.AIAgent
    import ai.koog.agents.core.agent.functionalStrategy
    import ai.koog.prompt.executor.llms.all.simpleOllamaAIExecutor
    import ai.koog.prompt.executor.ollama.client.OllamaModels
    import kotlinx.coroutines.runBlocking
    -->
    ```kotlin
    val strategy = functionalStrategy<String, String> { input ->
        val response = requestLLM(input)
        response.asAssistantMessage().content
    }

    val mathAgent = AIAgent(
        promptExecutor = simpleOllamaAIExecutor(),
        llmModel = OllamaModels.Meta.LLAMA_3_2,
        strategy = strategy
    )

    fun main() = runBlocking {
        val result = mathAgent.run("What is 12 × 9?")
        println(result)
    }
    ```
    <!--- KNIT example-functional-agent-01.kt -->

=== "Java"

    <!--- INCLUDE
    /**
    -->
    <!--- SUFFIX
    **/
    -->
    ```java
    AIAgent<String, String> mathAgent = AIAgent.builder()
        .promptExecuto

*[truncated — see source for full prompt]*