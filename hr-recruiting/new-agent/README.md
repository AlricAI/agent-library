# New Agent

> This guide will walk you through the steps to build high-quality agents by extending the `Agent` class.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How to Create Good Agents

This guide will walk you through the steps to build high-quality agents by extending the `Agent` class. It emphasizes best practices, the use of type annotations, comprehensive documentation, and modular design to ensure maintainability and scalability. Additionally, you will learn how to incorporate a callable `llm` parameter or specify a `model_name` attribute to enhance flexibility and functionality. These principles ensure that agents are not only functional but also robust and adaptable to future requirements.

## Overview

A good agent is a modular and reusable component designed to perform specific tasks efficiently. By inheriting from the base `Agent` class, developers can extend its functionality while adhering to standardized principles. Each custom agent should:

- Inherit from the `Agent` class to maintain compatibility with swarms.
- Define a `run(task: str, img: str)` method to execute tasks effectively.
- Include descriptive attributes such as `name`, `system_prompt`, and `description` to enhance clarity.
- Optionally, include an `llm` parameter (callable) or a `model_name` to enable seamless integration with language models.
- Emphasize modularity, allowing the agent to be reused across various contexts and tasks.

By following these guidelines, you can create agents that integrate well with broader systems and exhibit high reliability in real-world applications.

---

## Creating a Custom Agent

Here is a detailed template for creating a custom agent by inheriting the `Agent` class. This template demonstrates how to structure an agent with extendable and reusable features:

```python
from typing import Callable, Any
from swarms import Agent

class MyNewAgent(Agent):
    """
    A custom agent class for specialized tasks.

    Attributes:
        name (str): The name of the agent.
        system_prompt (str): The prompt guiding the agent's behavior.
        description (str): A brief description of the agent's purpose.
  

*[truncated — see source for full prompt]*