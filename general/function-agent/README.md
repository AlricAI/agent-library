# Function Agent

> from typing import List, Optional, Sequence

from llama_index.core.agent.workflow.agent_context import AgentContext
from llama_index.core.agent.workfl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import List, Optional, Sequence

from llama_index.core.agent.workflow.agent_context import AgentContext
from llama_index.core.agent.workflow.base_agent import BaseWorkflowAgent
from llama_index.core.agent.workflow.workflow_events import (
    AgentInput,
    AgentOutput,
    AgentStream,
    ToolCallResult,
)
from llama_index.core.base.llms.types import ChatResponse
from llama_index.core.bridge.pydantic import BaseModel, Field
from llama_index.core.llms import ChatMessage
from llama_index.core.memory import BaseMemory
from llama_index.core.tools import AsyncBaseTool
from llama_index.core.workflow import Context


class FunctionAgent(BaseWorkflowAgent):
    """Function calling agent implementation."""

    scratchpad_key: str = "scratchpad"
    initial_tool_choice: Optional[str] = Field(
        default=None,
        description="The tool to try and force to call on the first iteration of the agent.",
    )
    allow_parallel_tool_calls: bool = Field(
        default=True,
        description="If True, the agent will call multiple tools in parallel. If False, the agent will call tools sequentially.",
    )

    async def _get_response(
        self, current_llm_input: List[ChatMessage], tools: Sequence[AsyncBaseTool]
    ) -> ChatResponse:
        chat_kwargs = {
            "chat_history": current_llm_input,
            "allow_parallel_tool_calls": self.allow_parallel_tool_calls,
            "tools": tools,
        }

        # Only add tool choice if set and if its the first response
        if (
            self.initial_tool_choice is not None
            and current_llm_input[-1].role == "user"
        ):
            chat_kwargs["tool_choice"] = self.initial_tool_choice

        return await self.llm.achat_with_tools(  # type: ignore
            **chat_kwargs
        )

    async def _get_streaming_response(
        self,
        ctx: AgentContext,
        current_llm_input: List[ChatMessage],
        tools: Sequence[AsyncBaseTool],
    ) -> ChatRespo

*[truncated — see source for full prompt]*