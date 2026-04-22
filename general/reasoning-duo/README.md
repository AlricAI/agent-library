# Reasoning Duo

> The ReasoningDuo class implements a dual-agent reasoning system that combines a reasoning agent and a main agent to provide well-thought-out responses to complex tasks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ReasoningDuo

The ReasoningDuo class implements a dual-agent reasoning system that combines a reasoning agent and a main agent to provide well-thought-out responses to complex tasks. This architecture enables more robust and reliable outputs by separating the reasoning process from the final response generation.


## Class Overview

### Constructor Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| model_name | str | "reasoning-agent-01" | Name identifier for the reasoning agent |
| description | str | "A highly intelligent..." | Description of the reasoning agent's capabilities |
| model_names | list[str] | ["gpt-5.4", "gpt-4.1"] | Model names for reasoning and main agents |
| system_prompt | str | "You are a helpful..." | System prompt for the main agent |

### Methods

| Method | Parameters | Returns | Description |
|--------|------------|---------|-------------|
| run | task: str | str | Processes a single task through both agents |
| batched_run | tasks: List[str] | List[str] | Processes multiple tasks sequentially |



## Quick Start

```python
from swarms.agents.reasoning_duo import ReasoningDuo

# Initialize the ReasoningDuo
duo = ReasoningDuo(
    model_name="reasoning-agent-01",
    model_names=["gpt-5.4", "gpt-4.1"]
)

# Run a single task
result = duo.run("Explain the concept of gravitational waves")

# Run multiple tasks
tasks = [
    "Calculate compound interest for $1000 over 5 years",
    "Explain quantum entanglement"
]
results = duo.batched_run(tasks)
```

## Examples

### 1. Mathematical Analysis

```python
duo = ReasoningDuo()

# Complex mathematical problem
math_task = """
Solve the following differential equation:
dy/dx + 2y = x^2, y(0) = 1
"""

solution = duo.run(math_task)
```

### 2. Physics Problem

```python
# Quantum mechanics problem
physics_task = """
Calculate the wavelength of an electron with kinetic energy of 50 eV 
using the de Broglie relationship.
"""

result = duo.run(physics

*[truncated — see source for full prompt]*