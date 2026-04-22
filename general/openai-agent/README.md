#  Openai Agent

> import asyncio
import logging
from typing import (
    Any,
    AsyncGenerator,
    Dict,
    Iterable,
    List,
    Literal,
    Mapping,
    Option

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import logging
from typing import (
    Any,
    AsyncGenerator,
    Dict,
    Iterable,
    List,
    Literal,
    Mapping,
    Optional,
    Sequence,
    Type,
    Union,
    cast,
)

from autogen_agentchat import EVENT_LOGGER_NAME
from autogen_agentchat.agents import BaseChatAgent
from autogen_agentchat.base import Response
from autogen_agentchat.messages import (
    AgentEvent,
    BaseChatMessage,
    ChatMessage,
    HandoffMessage,
    MultiModalMessage,
    StopMessage,
    TextMessage,
    ToolCallSummaryMessage,
)
from autogen_core import CancellationToken, Component
from autogen_core.models import UserMessage
from pydantic import BaseModel, Field
from typing_extensions import NotRequired, TypedDict

from openai import AsyncAzureOpenAI, AsyncOpenAI  # type: ignore

# Number of characters to display when previewing image content in logs and UI
# Base64 encoded images can be very long, so we truncate for readability
IMAGE_CONTENT_PREVIEW_LENGTH = 50

# NOTE: We use the new Responses API, so ChatCompletion imports are not needed.

event_logger = logging.getLogger(EVENT_LOGGER_NAME)


# TypedDict classes for built-in tool configurations
class FileSearchToolConfig(TypedDict):
    """Configuration for file_search tool."""

    type: Literal["file_search"]
    vector_store_ids: List[str]  # required - The IDs of the vector stores to search
    max_num_results: NotRequired[int]  # optional
    ranking_options: NotRequired[Dict[str, Any]]  # optional
    filters: NotRequired[Dict[str, Any]]  # optional


class WebSearchToolConfig(TypedDict):
    """Configuration for web_search_preview tool."""

    type: Literal["web_search_preview"]
    search_context_size: NotRequired[str]  # optional
    user_location: NotRequired[Union[str, Dict[str, Any]]]  # optional - Can be string or structured location


class ComputerUseToolConfig(TypedDict):
    """Configuration for computer_use_preview tool."""

    type: Literal["computer_use_preview"]
    display_heig

*[truncated — see source for full prompt]*