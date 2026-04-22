# Goap Agents

> GOAP 是一種演算法規劃方法，使用 [A* 搜尋][A* search] 來尋找最佳操作序列，在滿足目標條件的同時將總成本降至最低。
與使用 LLM 產生計畫的 [基於 LLM 的規劃器](llm-based-planners.md) 不同，GOAP agent 透過演算法根據預定義的目標和操作來

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GOAP agent

GOAP 是一種演算法規劃方法，使用 [A* 搜尋][A* search] 來尋找最佳操作序列，在滿足目標條件的同時將總成本降至最低。
與使用 LLM 產生計畫的 [基於 LLM 的規劃器](llm-based-planners.md) 不同，GOAP agent 透過演算法根據預定義的目標和操作來發現操作序列。

GOAP 規劃器涉及三個主要概念：

- **狀態**：代表世界的目前狀態。
- **操作**：定義可以執行的內容，包括前提條件、效果（信念）、成本和執行邏輯。
- **目標**：定義目標條件、啟發式成本和值函數。

??? note "先決條件"

    --8<-- "quickstart-snippets.md:prerequisites"

    --8<-- "quickstart-snippets.md:dependencies"

    --8<-- "quickstart-snippets.md:api-key"

    本頁面中的範例假設您已設定 `OPENAI_API_KEY` 環境變數。

在 Koog 中，您可以使用 DSL 透過宣告式地指定目標和操作來定義 GOAP agent。

若要建立 GOAP agent，您需要：

1. 將狀態定義為一個 data class，其屬性代表特定於您目標的各個面向。
2. 使用 [goap()](https://api.koog.ai/agents/agents-planner/ai.koog.agents.planner.goap/goap.html) 函式建立 [GOAPPlanner](https://api.koog.ai/agents/agents-planner/ai.koog.agents.planner.goap/-g-o-a-p-planner/index.html) 執行個體。
    1. 使用 [action()](https://api.koog.ai/agents/agents-planner/ai.koog.agents.planner.goap/-g-o-a-p-planner-builder/action.html) 函式定義具有前提條件和信念的操作。
    2. 使用 [goal()](https://api.koog.ai/agents/agents-planner/ai.koog.agents.planner.goap/-g-o-a-p-planner-builder/goal.html) 函式定義具有完成條件的目標。
3. 使用 [AIAgentPlannerStrategy](https://api.koog.ai/agents/agents-planner/ai.koog.agents.planner/-a-i-agent-planner-strategy/index.html) 包裝規劃器，並將其傳遞給 [PlannerAIAgent](https://api.koog.ai/agents/agents-planner/ai.koog.agents.planner/-planner-a-i-agent/index.html) 建構函式。

!!! note

    規劃器選擇單個操作及其序列。
    每個操作都包含一個在執行操作前必須成立的前提條件，以及一個定義預測結果的信念。
    欲了解更多關於信念的資訊，請參閱[狀態信念與實際執行的比較](#state-beliefs-compared-to-actual-execution)。

在以下範例中，GOAP 處理建立文章的高階規劃（大綱 → 草稿 → 審查 → 發佈），而 LLM 則在每個操作中執行實際的內容產生。

=== "Kotlin"

    <!--- INCLUDE
    import ai.koog.agents.core.agent.AIAgent
    import ai.koog.agents.core.agent.config.AIAgentConfig
    import ai.koog.agents.planner.AIAgentPlannerStrategy
    import ai.koog.agents.planner.goap.GoapAgentState
    import ai.koog.prompt.dsl.prompt
    import ai.koog.prompt.executor.clients.openai.OpenAIModels
    import ai.koog.prompt.executor.llms.all.simpleOpenAI

*[truncated — see source for full prompt]*