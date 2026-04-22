# Functional Agents

> 함수형 에이전트를 사용하면 사용자 입력을 처리하고, LLM과 상호작용하며, 필요한 경우 도구를 호출하고, 최종 출력을 생성하는 로직을 하나의 함수로 구현합니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 함수형 에이전트 (Functional agents)

함수형 에이전트를 사용하면 사용자 입력을 처리하고, LLM과 상호작용하며, 필요한 경우 도구를 호출하고, 최종 출력을 생성하는 로직을 하나의 함수로 구현합니다.
[그래프 기반 에이전트](graph-based-agents.md)와 비교했을 때, 이는 보통 다음과 같은 단점이 있지만 더 빠른 프로토타이핑이 가능함을 의미합니다:

- 시각화가 쉽지 않음
- 상태 유지(state persistence)가 없음

??? note "사전 요구 사항 (Prerequisites)"

    --8<-- "quickstart-snippets.md:prerequisites"

    --8<-- "quickstart-snippets.md:dependencies"

    --8<-- "quickstart-snippets.md:api-key"

    이 페이지의 예제들은 Ollama를 통해 로컬에서 Llama 3.2를 실행하고 있다고 가정합니다.

이 페이지에서는 에이전트를 위한 커스텀 로직을 빠르게 프로토타이핑하기 위해 함수형 전략을 구현하는 방법을 설명합니다.

## 최소한의 함수형 에이전트 생성하기

최소한의 함수형 에이전트를 만들려면, [기본 에이전트](basic-agents.md)와 동일하게 [`AIAgent`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent/index.html) 인터페이스를 사용하고 [`AIAgentFunctionalStrategy`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent-functional-strategy/index.html) 인스턴스를 전달합니다.
입력을 받아 출력을 반환하고, 한 번의 LLM 호출을 수행한 후 응답에서 어시스턴트 메시지의 내용을 반환하는 함수형 전략을 정의할 수 있습니다.

Kotlin에서는 `functionalStrategy {...}` DSL 메서드를 사용하는 것이 가장 편리합니다. Java에서는 `AIAgent` 빌더의 `functionalStrategy` 메서드를 사용할 수 있습니다.

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
    <!--- SUFFI

*[truncated — see source for full prompt]*