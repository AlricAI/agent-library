#  Code Executor Agent

> import logging
import re
from inspect import iscoroutinefunction
from typing import (
    AsyncGenerator,
    Awaitable,
    Callable,
    List,
    O

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import logging
import re
from inspect import iscoroutinefunction
from typing import (
    AsyncGenerator,
    Awaitable,
    Callable,
    List,
    Optional,
    Sequence,
    Union,
    cast,
)

from autogen_core import CancellationToken, Component, ComponentModel
from autogen_core.code_executor import CodeBlock, CodeExecutor, CodeResult
from autogen_core.model_context import (
    ChatCompletionContext,
    UnboundedChatCompletionContext,
)
from autogen_core.models import (
    AssistantMessage,
    ChatCompletionClient,
    CreateResult,
    LLMMessage,
    SystemMessage,
    UserMessage,
)
from pydantic import BaseModel
from typing_extensions import Self

from .. import EVENT_LOGGER_NAME
from ..base import Response
from ..messages import (
    BaseAgentEvent,
    BaseChatMessage,
    CodeExecutionEvent,
    CodeGenerationEvent,
    HandoffMessage,
    ModelClientStreamingChunkEvent,
    TextMessage,
    ThoughtEvent,
)
from ..utils import remove_images
from ._base_chat_agent import BaseChatAgent

event_logger = logging.getLogger(EVENT_LOGGER_NAME)


class CodeExecutorAgentConfig(BaseModel):
    """Configuration for CodeExecutorAgent"""

    name: str
    code_executor: ComponentModel
    model_client: ComponentModel | None = None
    description: str | None = None
    sources: List[str] | None = None
    system_message: str | None = None
    model_client_stream: bool = False
    model_context: ComponentModel | None = None
    supported_languages: List[str] | None = None


class RetryDecision(BaseModel):
    reason: str
    retry: bool


class ApprovalRequest(BaseModel):
    """Request for approval of code execution."""

    code: str
    context: List[LLMMessage]


class ApprovalResponse(BaseModel):
    """Response to approval request."""

    approved: bool
    reason: str


# Type aliases for approval functions
SyncApprovalFunc = Callable[[ApprovalRequest], ApprovalResponse]
AsyncApprovalFunc = Callable[[ApprovalRequest], Awaitable[ApprovalResponse]]
Approval

*[truncated — see source for full prompt]*