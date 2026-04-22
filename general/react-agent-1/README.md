# React Agent

> import uuid
from typing import List, Sequence, Optional, cast

from llama_index.core.agent.react.formatter import ReActChatFormatter
from llama_index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import uuid
from typing import List, Sequence, Optional, cast

from llama_index.core.agent.react.formatter import ReActChatFormatter
from llama_index.core.agent.react.output_parser import ReActOutputParser
from llama_index.core.agent.react.prompts import CONTEXT_REACT_CHAT_SYSTEM_HEADER
from llama_index.core.agent.react.types import (
    ActionReasoningStep,
    BaseReasoningStep,
    ObservationReasoningStep,
    ResponseReasoningStep,
)
from llama_index.core.agent.workflow.agent_context import AgentContext
from llama_index.core.agent.workflow.base_agent import BaseWorkflowAgent
from llama_index.core.agent.workflow.workflow_events import (
    AgentInput,
    AgentOutput,
    AgentStream,
    ToolCallResult,
)
from llama_index.core.base.llms.types import ChatResponse, TextBlock
from llama_index.core.bridge.pydantic import BaseModel, Field, model_validator
from llama_index.core.llms import ChatMessage
from llama_index.core.llms.llm import ToolSelection
from llama_index.core.memory import BaseMemory
from llama_index.core.prompts.base import PromptTemplate
from llama_index.core.prompts.mixin import PromptDictType
from llama_index.core.tools import AsyncBaseTool
from llama_index.core.workflow import Context


def default_formatter(fields: Optional[dict] = None) -> ReActChatFormatter:
    """Sets up a default formatter so that the proper react header is set."""
    fields = fields or {}
    return ReActChatFormatter.from_defaults(context=fields.get("system_prompt", None))


class ReActAgent(BaseWorkflowAgent):
    """React agent implementation."""

    reasoning_key: str = "current_reasoning"
    output_parser: ReActOutputParser = Field(
        default_factory=ReActOutputParser, description="The react output parser"
    )
    formatter: ReActChatFormatter = Field(
        default_factory=default_formatter,
        description="The react chat formatter to format the reasoning steps and chat history into an llm input.",
    )

    @model_validator(mode="after")
    def 

*[truncated — see source for full prompt]*