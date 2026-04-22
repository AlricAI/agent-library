# Consistency Agent

> The `SelfConsistencyAgent` is a specialized agent designed for generating multiple independent responses to a given task and aggregating them into a single, consistent final answer.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Consistency Agent Documentation

The `SelfConsistencyAgent` is a specialized agent designed for generating multiple independent responses to a given task and aggregating them into a single, consistent final answer. It leverages concurrent processing to enhance efficiency and employs a majority voting mechanism to ensure the reliability of the aggregated response.

## Purpose

The primary objective of the `SelfConsistencyAgent` is to provide a robust mechanism for decision-making and problem-solving by generating diverse responses and synthesizing them into a coherent final answer. This approach is particularly useful in scenarios where consistency and reliability are critical.

## Class: `SelfConsistencyAgent`

### Initialization

- **`__init__`**: Initializes the `SelfConsistencyAgent` with specified parameters.

#### Arguments

| Argument               | Type    | Default | Description                                                                 |
|------------------------|---------|---------|-----------------------------------------------------------------------------|
| `name`                 | `str`   | `"Self-Consistency-Agent"` | Name of the agent.                                                         |
| `description`          | `str`   | `"An agent that uses self consistency to generate a final answer."` | Description of the agent's purpose.                                        |
| `system_prompt`        | `str`   | `CONSISTENCY_SYSTEM_PROMPT` | System prompt for the reasoning agent.                                     |
| `model_name`           | `str`   | Required | The underlying language model to use.                                      |
| `num_samples`          | `int`   | `5`     | Number of independent responses to generate.                               |
| `max_loops`            | `int`   | `1`     | Maximum number of reasoning loops per sample.                              |
| `majority_voting_prompt` | `Optional[str]` | `majority_votin

*[truncated — see source for full prompt]*