#  User Proxy Agent

> import asyncio
import uuid
from contextlib import contextmanager
from contextvars import ContextVar
from inspect import iscoroutinefunction
from typin

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import uuid
from contextlib import contextmanager
from contextvars import ContextVar
from inspect import iscoroutinefunction
from typing import Any, AsyncGenerator, Awaitable, Callable, ClassVar, Generator, Optional, Sequence, Union, cast

from autogen_core import CancellationToken, Component
from pydantic import BaseModel
from typing_extensions import Self

from ..base import Response
from ..messages import BaseAgentEvent, BaseChatMessage, HandoffMessage, TextMessage, UserInputRequestedEvent
from ._base_chat_agent import BaseChatAgent

SyncInputFunc = Callable[[str], str]
AsyncInputFunc = Callable[[str, Optional[CancellationToken]], Awaitable[str]]
InputFuncType = Union[SyncInputFunc, AsyncInputFunc]


# TODO: check if using to_thread fixes this in jupyter
async def cancellable_input(prompt: str, cancellation_token: Optional[CancellationToken]) -> str:
    task: asyncio.Task[str] = asyncio.create_task(asyncio.to_thread(input, prompt))
    if cancellation_token is not None:
        cancellation_token.link_future(task)
    return await task


class UserProxyAgentConfig(BaseModel):
    """Declarative configuration for the UserProxyAgent."""

    name: str
    description: str = "A human user"
    input_func: str | None = None


class UserProxyAgent(BaseChatAgent, Component[UserProxyAgentConfig]):
    """An agent that can represent a human user through an input function.

    This agent can be used to represent a human user in a chat system by providing a custom input function.

    .. note::

        Using :class:`UserProxyAgent` puts a running team in a temporary blocked
        state until the user responds. So it is important to time out the user input
        function and cancel using the :class:`~autogen_core.CancellationToken` if the user does not respond.
        The input function should also handle exceptions and return a default response if needed.

        For typical use cases that involve
        slow human responses, it is recommended to u

*[truncated — see source for full prompt]*