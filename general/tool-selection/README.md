# Tool Selection

> """LLM-based tool selector middleware.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""LLM-based tool selector middleware."""

from __future__ import annotations

import logging
from dataclasses import dataclass
from typing import TYPE_CHECKING, Annotated, Any, Literal, Union

from langchain_core.language_models.chat_models import BaseChatModel
from langchain_core.messages import AIMessage, HumanMessage
from pydantic import Field, TypeAdapter
from typing_extensions import TypedDict

from langchain.agents.middleware.types import (
    AgentMiddleware,
    AgentState,
    ContextT,
    ModelRequest,
    ModelResponse,
    ResponseT,
)
from langchain.chat_models.base import init_chat_model

if TYPE_CHECKING:
    from collections.abc import Awaitable, Callable

    from langchain.tools import BaseTool

logger = logging.getLogger(__name__)

DEFAULT_SYSTEM_PROMPT = (
    "Your goal is to select the most relevant tools for answering the user's query."
)


@dataclass
class _SelectionRequest:
    """Prepared inputs for tool selection."""

    available_tools: list[BaseTool]
    system_message: str
    last_user_message: HumanMessage
    model: BaseChatModel
    valid_tool_names: list[str]


def _create_tool_selection_response(tools: list[BaseTool]) -> TypeAdapter[Any]:
    """Create a structured output schema for tool selection.

    Args:
        tools: Available tools to include in the schema.

    Returns:
        `TypeAdapter` for a schema where each tool name is a `Literal` with its
            description.

    Raises:
        AssertionError: If `tools` is empty.
    """
    if not tools:
        msg = "Invalid usage: tools must be non-empty"
        raise AssertionError(msg)

    # Create a Union of Annotated Literal types for each tool name with description
    # For instance: Union[Annotated[Literal["tool1"], Field(description="...")], ...]
    literals = [
        Annotated[Literal[tool.name], Field(description=tool.description)] for tool in tools
    ]
    selected_tool_type = Union[tuple(literals)]  # type: ignore[valid-type]  # noqa: UP007

   

*[truncated — see source for full prompt]*