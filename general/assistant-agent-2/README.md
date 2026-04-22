#  Assistant Agent

> from __future__ import annotations

import asyncio
import json
import logging
import uuid
import warnings
from typing import (
    Any,
    AsyncGener

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

import asyncio
import json
import logging
import uuid
import warnings
from typing import (
    Any,
    AsyncGenerator,
    Awaitable,
    Callable,
    Dict,
    List,
    Mapping,
    Optional,
    Sequence,
    Tuple,
    TypeVar,
    Union,
)

from autogen_core import CancellationToken, Component, ComponentModel, FunctionCall
from autogen_core.memory import Memory
from autogen_core.model_context import (
    ChatCompletionContext,
    UnboundedChatCompletionContext,
)
from autogen_core.models import (
    AssistantMessage,
    ChatCompletionClient,
    CreateResult,
    FunctionExecutionResult,
    FunctionExecutionResultMessage,
    LLMMessage,
    SystemMessage,
)
from autogen_core.tools import BaseTool, FunctionTool, StaticStreamWorkbench, ToolResult, Workbench
from pydantic import BaseModel, Field
from typing_extensions import Self

from .. import EVENT_LOGGER_NAME
from ..base import Handoff as HandoffBase
from ..base import Response
from ..messages import (
    BaseAgentEvent,
    BaseChatMessage,
    HandoffMessage,
    MemoryQueryEvent,
    ModelClientStreamingChunkEvent,
    StructuredMessage,
    StructuredMessageFactory,
    TextMessage,
    ThoughtEvent,
    ToolCallExecutionEvent,
    ToolCallRequestEvent,
    ToolCallSummaryMessage,
)
from ..state import AssistantAgentState
from ..utils import remove_images
from ._base_chat_agent import BaseChatAgent

event_logger = logging.getLogger(EVENT_LOGGER_NAME)

# Add type variables for more specific typing
T = TypeVar("T", bound=BaseModel)
R = TypeVar("R", bound=BaseModel)


class AssistantAgentConfig(BaseModel):
    """The declarative configuration for the assistant agent."""

    name: str
    model_client: ComponentModel
    tools: List[ComponentModel] | None = None
    workbench: List[ComponentModel] | None = None
    handoffs: List[HandoffBase | str] | None = None
    model_context: ComponentModel | None = None
    memory: List[ComponentModel] | None = None
    descr

*[truncated — see source for full prompt]*