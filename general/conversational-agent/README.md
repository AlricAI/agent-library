# Conversational Agent

> from __future__ import annotations

import logging
from string import Template
from typing import Any, Dict, List, Optional, Union

from colorama impo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

import logging
from string import Template
from typing import Any, Dict, List, Optional, Union

from colorama import Fore

from autochain.agent.base_agent import BaseAgent
from autochain.agent.conversational_agent.output_parser import ConvoJSONOutputParser
from autochain.agent.conversational_agent.prompt import (
    CLARIFYING_QUESTION_PROMPT_TEMPLATE,
    PLANNING_PROMPT_TEMPLATE,
    SHOULD_ANSWER_PROMPT_TEMPLATE,
    FIX_TOOL_INPUT_PROMPT_TEMPLATE,
)
from autochain.agent.message import BaseMessage, ChatMessageHistory, UserMessage
from autochain.agent.prompt_formatter import JSONPromptTemplate
from autochain.agent.structs import AgentAction, AgentFinish
from autochain.models.base import BaseLanguageModel, Generation
from autochain.tools.base import Tool
from autochain.utils import print_with_color

logger = logging.getLogger(__name__)


class ConversationalAgent(BaseAgent):
    """
    Conversational agent who can use tools available to make a conversation by following
    the conversational planning prompt
    """

    output_parser: ConvoJSONOutputParser = ConvoJSONOutputParser()
    llm: BaseLanguageModel = None
    prompt_template: JSONPromptTemplate = None
    allowed_tools: Dict[str, Tool] = {}
    tools: List[Tool] = []

    # Optionally you could set a prompt for this conversational agent or directly update the prompt
    prompt: str = ""

    @classmethod
    def from_llm_and_tools(
        cls,
        llm: BaseLanguageModel,
        tools: Optional[List[Tool]] = None,
        output_parser: Optional[ConvoJSONOutputParser] = None,
        prompt_template: str = PLANNING_PROMPT_TEMPLATE,
        input_variables: Optional[List[str]] = None,
        prompt: str = "",
        **kwargs: Any,
    ) -> ConversationalAgent:
        """Construct an agent from an LLM and tools."""
        tools = tools or []

        template = cls.get_prompt_template(
            template=prompt_template,
            input_variables=input_vari

*[truncated — see source for full prompt]*