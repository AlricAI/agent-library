#  Base Chat Agent

> from abc import ABC, abstractmethod
from typing import Any, AsyncGenerator, List, Mapping, Sequence

from autogen_core import CancellationToken, Compo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from abc import ABC, abstractmethod
from typing import Any, AsyncGenerator, List, Mapping, Sequence

from autogen_core import CancellationToken, ComponentBase, trace_create_agent_span, trace_invoke_agent_span
from pydantic import BaseModel

from ..base import ChatAgent, Response, TaskResult
from ..messages import (
    BaseAgentEvent,
    BaseChatMessage,
    ModelClientStreamingChunkEvent,
    TextMessage,
)
from ..state import BaseState


class BaseChatAgent(ChatAgent, ABC, ComponentBase[BaseModel]):
    """Base class for a chat agent.

    This abstract class provides a base implementation for a :class:`ChatAgent`.
    To create a new chat agent, subclass this class and implement the
    :meth:`on_messages`, :meth:`on_reset`, and :attr:`produced_message_types`.
    If streaming is required, also implement the :meth:`on_messages_stream` method.

    An agent is considered stateful and maintains its state between calls to
    the :meth:`on_messages` or :meth:`on_messages_stream` methods.
    The agent should store its state in the
    agent instance. The agent should also implement the :meth:`on_reset` method
    to reset the agent to its initialization state.

    .. note::

        The caller should only pass the new messages to the agent on each call
        to the :meth:`on_messages` or :meth:`on_messages_stream` method.
        Do not pass the entire conversation history to the agent on each call.
        This design principle must be followed when creating a new agent.
    """

    component_type = "agent"

    def __init__(self, name: str, description: str) -> None:
        """Initialize the agent with a name and description."""
        with trace_create_agent_span(
            agent_name=name,
            agent_description=description,
        ):
            self._name = name
            if self._name.isidentifier() is False:
                raise ValueError("The agent name must be a valid Python identifier.")
            self._description = description

  

*[truncated — see source for full prompt]*