# Builder Agent

> """
Builder Agent.

Claude Agent SDK-powered coding agent for Busibox app builder workflows.
"""

import asyncio
import logging
from typing import Any

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Builder Agent.

Claude Agent SDK-powered coding agent for Busibox app builder workflows.
"""

import asyncio
import logging
from typing import Any, Dict, Optional
from pathlib import Path

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    ToolStrategy,
)
from app.schemas.streaming import complete, content, error, thought, tool_result, tool_start

from .builder_prompts import BUILDER_SYSTEM_PROMPT

logger = logging.getLogger(__name__)

try:
    from claude_agent_sdk import ClaudeAgentOptions, query
except Exception:  # pragma: no cover - handled at runtime
    ClaudeAgentOptions = None
    query = None


class BuilderAgent(BaseStreamingAgent):
    """
    Builder agent that delegates coding execution to Claude Agent SDK.
    """

    def __init__(self):
        config = AgentConfig(
            name="builder-agent",
            display_name="Builder Agent",
            instructions=BUILDER_SYSTEM_PROMPT,
            tools=[],  # Claude Agent SDK provides native coding tools
            model="agent",
            execution_mode=ExecutionMode.RUN_ONCE,
            tool_strategy=ToolStrategy.LLM_DRIVEN,
            allow_frontier_fallback=True,
        )
        super().__init__(config)

    async def run_with_streaming(
        self,
        query_text: str,
        stream,
        cancel: asyncio.Event,
        context: Optional[dict] = None,
    ) -> str:
        """
        Execute Claude Agent SDK query and map streamed messages to Busibox StreamEvents.
        """
        if query is None or ClaudeAgentOptions is None:
            await stream(error(source=self.name, message="Claude Agent SDK is not available."))
            return "Claude Agent SDK is not available."

        agent_context = await self._setup_context(context, stream, query_text)
        if agent_context is None:
            return "Authentication or session error. Please sign in and try again."

        project_id = (agent_co

*[truncated — see source for full prompt]*