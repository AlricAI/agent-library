# Base Converter Adapter

> """Base converter adapter for structured output conversion.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Base converter adapter for structured output conversion."""

from __future__ import annotations

from abc import ABC, abstractmethod
import json
import re
from typing import TYPE_CHECKING, Final, Literal

from crewai.utilities.pydantic_schema_utils import (
    ModelDescription,
    generate_model_description,
)


if TYPE_CHECKING:
    from crewai.agents.agent_adapters.base_agent_adapter import BaseAgentAdapter
    from crewai.task import Task


_CODE_BLOCK_PATTERN: Final[re.Pattern[str]] = re.compile(
    r"```(?:json)?\s*([\s\S]*?)```"
)
_JSON_OBJECT_PATTERN: Final[re.Pattern[str]] = re.compile(r"\{[\s\S]*}")


class BaseConverterAdapter(ABC):
    """Abstract base class for converter adapters in CrewAI.

    Defines the common interface for converting agent outputs to structured formats.
    All converter adapters must implement the methods defined here.

    Attributes:
        agent_adapter: The agent adapter instance.
        _output_format: The expected output format (json, pydantic, or None).
        _schema: The schema description for the expected output.
    """

    def __init__(self, agent_adapter: BaseAgentAdapter) -> None:
        """Initialize the converter adapter.

        Args:
            agent_adapter: The agent adapter to configure for structured output.
        """
        self.agent_adapter = agent_adapter
        self._output_format: Literal["json", "pydantic"] | None = None
        self._schema: ModelDescription | None = None

    @abstractmethod
    def configure_structured_output(self, task: Task) -> None:
        """Configure agents to return structured output.

        Must support both JSON and Pydantic output formats.

        Args:
            task: The task requiring structured output.
        """

    @abstractmethod
    def enhance_system_prompt(self, base_prompt: str) -> str:
        """Enhance the system prompt with structured output instructions.

        Args:
            base_prompt: The original system prompt.

        Retu

*[truncated — see source for full prompt]*