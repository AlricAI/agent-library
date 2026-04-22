# MCP EVALUATION ARCHITECTURE DIAGRAM

> ## System Overview

```mermaid
graph TB
    subgraph "Generic Evaluation Core"
        TS[TestScenario]
        EF[MCPEvaluationFramework]
        MC[

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP Evaluation Framework - Architecture Diagrams

## System Overview

```mermaid
graph TB
    subgraph "Generic Evaluation Core"
        TS[TestScenario]
        EF[MCPEvaluationFramework]
        MC[MetricsCollector]
        RG[ReportGenerator]
        ER[EvaluationReport]
    end

    subgraph "Tool-Specific Adapters"
        TA[ToolAdapter Interface]
        SA[SerenaToolAdapter]
        CA[CopilotToolAdapter]
        FA[FutureToolAdapter]
    end

    subgraph "Configuration"
        TC[ToolConfiguration]
        SC[serena_config.yaml]
        CC[copilot_config.yaml]
    end

    TC --> EF
    SC --> SA
    CC --> CA
    TS --> EF
    EF --> MC
    EF --> TA
    TA -.implements.- SA
    TA -.implements.- CA
    TA -.implements.- FA
    MC --> RG
    RG --> ER

    style EF fill:#e1f5ff
    style TA fill:#fff4e1
    style TC fill:#f0f0f0
```

## Evaluation Flow

```mermaid
sequenceDiagram
    participant User
    participant Framework as MCPEvaluationFramework
    participant Adapter as ToolAdapter
    participant Executor as ScenarioExecutor
    participant Claude as Claude Code
    participant Collector as MetricsCollector
    participant Reporter as ReportGenerator

    User->>Framework: run_evaluation(scenarios, tool_config)
    Framework->>Adapter: load adapter from config

    loop For each scenario
        Note over Framework: Run baseline (tool disabled)
        Framework->>Adapter: disable()
        Framework->>Collector: start()
        Framework->>Executor: execute_task(prompt, codebase)
        Executor->>Claude: invoke with prompt
        Claude-->>Executor: execution result
        Executor-->>Framework: baseline_result
        Framework->>Collector: stop()
        Collector-->>Framework: baseline_metrics

        Note over Framework: Run enhanced (tool enabled)
        Framework->>Adapter: enable()
        Framework->>Collector: start()
        Framework->>Executor: execute_task(prompt, codebase)
        Executor->>Claude: invoke with prompt
    

*[truncated — see source for full prompt]*