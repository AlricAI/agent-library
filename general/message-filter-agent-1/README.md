#  Message Filter Agent

> from typing import AsyncGenerator, List, Literal, Optional, Sequence, Union

from autogen_core import CancellationToken, Component, ComponentModel
fro

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import AsyncGenerator, List, Literal, Optional, Sequence, Union

from autogen_core import CancellationToken, Component, ComponentModel
from pydantic import BaseModel

from autogen_agentchat.agents import BaseChatAgent
from autogen_agentchat.base import Response
from autogen_agentchat.messages import BaseAgentEvent, BaseChatMessage

# ------------------------------
# Message Filter Config
# ------------------------------


class PerSourceFilter(BaseModel):
    source: str
    position: Optional[Literal["first", "last"]] = None
    count: Optional[int] = None


class MessageFilterConfig(BaseModel):
    per_source: List[PerSourceFilter]


# ------------------------------
# Component Config
# ------------------------------


class MessageFilterAgentConfig(BaseModel):
    name: str
    wrapped_agent: ComponentModel
    filter: MessageFilterConfig


# ------------------------------
# Message Filter Agent
# ------------------------------


class MessageFilterAgent(BaseChatAgent, Component[MessageFilterAgentConfig]):
    """
    A wrapper agent that filters incoming messages before passing them to the inner agent.

    .. warning::

        This is an experimental feature, and the API will change in the future releases.

    This is useful in scenarios like multi-agent workflows where an agent should only
    process a subset of the full message history—for example, only the last message
    from each upstream agent, or only the first message from a specific source.

    Filtering is configured using :class:`MessageFilterConfig`, which supports:
    - Filtering by message source (e.g., only messages from "user" or another agent)
    - Selecting the first N or last N messages from each source
    - If position is `None`, all messages from that source are included

    This agent is compatible with both direct message passing and team-based execution
    such as :class:`~autogen_agentchat.teams.GraphFlow`.

    Example:
        >>> agent_a = MessageFilterAgent(
  

*[truncated — see source for full prompt]*