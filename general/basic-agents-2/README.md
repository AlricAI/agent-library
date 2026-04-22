# Basic Agents

> 기본 에이전트(Basic agent)는 대부분의 일반적인 유스케이스에 적합한 단순한 실행 흐름을 가진 미리 정의된 전략을 사용합니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 기본 에이전트

기본 에이전트(Basic agent)는 대부분의 일반적인 유스케이스에 적합한 단순한 실행 흐름을 가진 미리 정의된 전략을 사용합니다.
이 에이전트는 문자열 입력(질문, 요청 또는 작업 설명)을 받아 이를 설정된 LLM(대규모 언어 모델)으로 보냅니다.
LLM은 제공된 도구(tools)를 호출하기로 결정할 수 있습니다.
에이전트는 도구를 실행하고 그 결과를 다시 LLM으로 보냅니다.
이 과정은 LLM이 더 이상 도구 호출을 요청하지 않고 문자열 응답을 반환할 때까지 반복됩니다.
그 후 에이전트는 이 응답을 출력합니다.

[그래프 기반 에이전트](graph-based-agents.md)에서는 기본 에이전트가 사용하는 미리 정의된 전략 그래프를 다시 만드는 방법을 확인할 수 있습니다.

??? note "사전 요구 사항"

    --8<-- "quickstart-snippets.md:prerequisites"

    --8<-- "quickstart-snippets.md:dependencies"

    --8<-- "quickstart-snippets.md:api-key"

    이 페이지의 예제들은 `OPENAI_API_KEY` 환경 변수가 설정되어 있다고 가정합니다.

## 최소한의 에이전트 생성하기

가장 기본적인 에이전트를 생성하려면, [`AIAgent`](https://api.koog.ai/agents/agents-core/ai.koog.agents.core.agent/-a-i-agent/index.html)를 인스턴스화하고 [언어 모델](../model-capabilities.md#creating-a-model-llmodel-configuration)이 포함된 [프롬프트 실행기(prompt executor)](../prompts/prompt-executors.md)를 제공하세요.

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

    이 에이전트는 입력으로 문자열을 기대하고 출력으로 문자열을 반환합니다.
    에이전트를 실행하려면 사용자 입력과 함께 `run()` 함수를 사용하세요.

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
    ```ja

*[truncated — see source for full prompt]*