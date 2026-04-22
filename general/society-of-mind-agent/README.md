#  Society Of Mind Agent

> from typing import Any, AsyncGenerator, List, Mapping, Sequence

from autogen_core import CancellationToken, Component, ComponentModel
from autogen_co

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import Any, AsyncGenerator, List, Mapping, Sequence

from autogen_core import CancellationToken, Component, ComponentModel
from autogen_core.model_context import (
    ChatCompletionContext,
    UnboundedChatCompletionContext,
)
from autogen_core.models import ChatCompletionClient, LLMMessage, SystemMessage, UserMessage
from pydantic import BaseModel
from typing_extensions import Self

from autogen_agentchat.base import Response
from autogen_agentchat.state import SocietyOfMindAgentState

from ..base import TaskResult, Team
from ..messages import (
    BaseAgentEvent,
    BaseChatMessage,
    HandoffMessage,
    ModelClientStreamingChunkEvent,
    TextMessage,
)
from ._base_chat_agent import BaseChatAgent


class SocietyOfMindAgentConfig(BaseModel):
    """The declarative configuration for a SocietyOfMindAgent."""

    name: str
    team: ComponentModel
    model_client: ComponentModel
    description: str | None = None
    instruction: str | None = None
    response_prompt: str | None = None
    model_context: ComponentModel | None = None


class SocietyOfMindAgent(BaseChatAgent, Component[SocietyOfMindAgentConfig]):
    """An agent that uses an inner team of agents to generate responses.

    Each time the agent's :meth:`on_messages` or :meth:`on_messages_stream`
    method is called, it runs the inner team of agents and then uses the
    model client to generate a response based on the inner team's messages.
    Once the response is generated, the agent resets the inner team by
    calling :meth:`Team.reset`.

    Limit context size sent to the model:

    You can limit the number of messages sent to the model by setting
    the `model_context` parameter to a :class:`~autogen_core.model_context.BufferedChatCompletionContext`.
    This will limit the number of recent messages sent to the model and can be useful
    when the model has a limit on the number of tokens it can process.
    You can also create your own model context by subclassing
    :class

*[truncated — see source for full prompt]*