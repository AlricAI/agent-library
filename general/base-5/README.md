# Base

> """Chain that implements the ReAct paper from https://arxiv.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Chain that implements the ReAct paper from https://arxiv.org/pdf/2210.03629.pdf."""

from __future__ import annotations

from collections.abc import Sequence
from typing import TYPE_CHECKING, Any

from langchain_core._api import deprecated
from langchain_core.documents import Document
from langchain_core.language_models import BaseLanguageModel
from langchain_core.prompts import BasePromptTemplate
from langchain_core.tools import BaseTool, Tool
from pydantic import Field
from typing_extensions import override

from langchain_classic._api.deprecation import AGENT_DEPRECATION_WARNING
from langchain_classic.agents.agent import Agent, AgentExecutor, AgentOutputParser
from langchain_classic.agents.agent_types import AgentType
from langchain_classic.agents.react.output_parser import ReActOutputParser
from langchain_classic.agents.react.textworld_prompt import TEXTWORLD_PROMPT
from langchain_classic.agents.react.wiki_prompt import WIKI_PROMPT
from langchain_classic.agents.utils import validate_tools_single_input

if TYPE_CHECKING:
    from langchain_community.docstore.base import Docstore


_LOOKUP_AND_SEARCH_TOOLS = {"Lookup", "Search"}


@deprecated(
    "0.1.0",
    message=AGENT_DEPRECATION_WARNING,
    removal="1.0",
)
class ReActDocstoreAgent(Agent):
    """Agent for the ReAct chain."""

    output_parser: AgentOutputParser = Field(default_factory=ReActOutputParser)

    @classmethod
    @override
    def _get_default_output_parser(cls, **kwargs: Any) -> AgentOutputParser:
        return ReActOutputParser()

    @property
    def _agent_type(self) -> str:
        """Return Identifier of an agent type."""
        return AgentType.REACT_DOCSTORE

    @classmethod
    @override
    def create_prompt(cls, tools: Sequence[BaseTool]) -> BasePromptTemplate:
        """Return default prompt."""
        return WIKI_PROMPT

    @classmethod
    def _validate_tools(cls, tools: Sequence[BaseTool]) -> None:
        validate_tools_single_input(cls.__name__, tools)
        super

*[truncated — see source for full prompt]*