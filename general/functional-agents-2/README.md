# Functional Agents

> 使用功能型代理，您可以将逻辑实现为一个函数，用于处理用户输入、与 LLM 交互、在必要时调用工具并生成最终输出。
与[基于图的代理](graph-based-agents.md)相比，这通常意味着更快的原型设计，但也存在以下缺点：

- 不易可视化
- 无状态持久化

??? note "前提条件"

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 功能型代理

使用功能型代理，您可以将逻辑实现为一个函数，用于处理用户输入、与 LLM 交互、在必要时调用工具并生成最终输出。
与[基于图的代理](graph-based-agents.md)相比，这通常意味着更快的原型设计，但也存在以下缺点：

- 不易可视化
- 无状态持久化

??? note "前提条件"

    --8<-- "quickstart-snippets.md:prerequisites"

    --8<-- "quickstart-snippets.md:dependencies"

    --8<-- "quickstart-snippets.md:api-key"

    本页中的示例假设您正在通过 Ollama 在本地运行 Llama 3.2。

本页介绍了如何实现功能型策略，以便为您的代理快速构建某些自定义逻辑的原型。

## 创建最小功能型代理

要创建一个最小功能型代理，请使用与[基础代理](basic-agents.md)相同的 [`AIAgent`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent/index.html) 接口，并向其传递一个 [`AIAgentFunctionalStrategy`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent-functional-strategy/index.html) 实例。
您可以定义一个功能型策略，该策略接收输入并返回输出，进行一次 LLM 调用，然后从响应中返回助手消息的内容。

在 Kotlin 中，最便捷的方法是使用 `functionalStrategy {...}` DSL 方法。在 Java 中，您可以使用 `AIAgent` 构建器上的 `functionalStrategy` 方法。

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
        .promptExecutor(SimpleLLMExecutorsKt.simpleOllamaAIExecutor("http://localhost:11434"))
        .llmModel(OllamaModels.Meta.LLAMA_3_2)
        .functional

*[truncated — see source for full prompt]*