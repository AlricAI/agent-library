# Base

> """Attempt to implement MRKL systems as described in arxiv.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Attempt to implement MRKL systems as described in arxiv.org/pdf/2205.00445.pdf."""

from __future__ import annotations

from collections.abc import Callable, Sequence
from typing import Any, NamedTuple

from langchain_core._api import deprecated
from langchain_core.callbacks import BaseCallbackManager
from langchain_core.language_models import BaseLanguageModel
from langchain_core.prompts import PromptTemplate
from langchain_core.tools import BaseTool, Tool
from langchain_core.tools.render import render_text_description
from pydantic import Field
from typing_extensions import override

from langchain_classic._api.deprecation import AGENT_DEPRECATION_WARNING
from langchain_classic.agents.agent import Agent, AgentExecutor, AgentOutputParser
from langchain_classic.agents.agent_types import AgentType
from langchain_classic.agents.mrkl.output_parser import MRKLOutputParser
from langchain_classic.agents.mrkl.prompt import FORMAT_INSTRUCTIONS, PREFIX, SUFFIX
from langchain_classic.agents.utils import validate_tools_single_input
from langchain_classic.chains import LLMChain


class ChainConfig(NamedTuple):
    """Configuration for a chain to use in MRKL system.

    Args:
        action_name: Name of the action.
        action: Action function to call.
        action_description: Description of the action.
    """

    action_name: str
    action: Callable
    action_description: str


@deprecated(
    "0.1.0",
    message=AGENT_DEPRECATION_WARNING,
    removal="1.0",
)
class ZeroShotAgent(Agent):
    """Agent for the MRKL chain.

    Args:
        output_parser: Output parser for the agent.
    """

    output_parser: AgentOutputParser = Field(default_factory=MRKLOutputParser)

    @classmethod
    @override
    def _get_default_output_parser(cls, **kwargs: Any) -> AgentOutputParser:
        return MRKLOutputParser()

    @property
    def _agent_type(self) -> str:
        """Return Identifier of agent type."""
        return AgentType.ZERO_SHOT_REACT_DESCRIPTION

    @

*[truncated — see source for full prompt]*