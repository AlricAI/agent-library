# Builder Local Agent

> """
Builder Local Agent.

Local-model fallback agent that executes Aider against the project workspace.
"""

import asyncio
import logging
import os
f

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Builder Local Agent.

Local-model fallback agent that executes Aider against the project workspace.
"""

import asyncio
import logging
import os
from pathlib import Path
from typing import Optional

from app.agents.base_agent import (
    AgentConfig,
    BaseStreamingAgent,
    ExecutionMode,
    ToolStrategy,
)
from app.schemas.streaming import complete, content, error, thought

logger = logging.getLogger(__name__)


class BuilderLocalAgent(BaseStreamingAgent):
    def __init__(self):
        config = AgentConfig(
            name="builder-local-agent",
            display_name="Builder Local Agent",
            instructions="Local model coding assistant using Aider.",
            tools=[],
            model="fast",
            execution_mode=ExecutionMode.RUN_ONCE,
            tool_strategy=ToolStrategy.LLM_DRIVEN,
        )
        super().__init__(config)

    async def run_with_streaming(
        self,
        query: str,
        stream,
        cancel: asyncio.Event,
        context: Optional[dict] = None,
    ) -> str:
        agent_context = await self._setup_context(context, stream, query)
        if agent_context is None:
            return "Authentication or session error."

        metadata = agent_context.metadata or {}
        project_id = metadata.get("projectId")
        if not project_id:
            await stream(error(source=self.name, message="Missing required metadata: projectId"))
            return "Missing required metadata: projectId"

        project_dir = Path("/srv/projects") / str(project_id)
        if not project_dir.exists():
            await stream(error(source=self.name, message=f"Project directory not found: {project_dir}"))
            return f"Project directory not found: {project_dir}"

        model = os.getenv("BUILDER_LOCAL_MODEL", "openai/fast")
        openai_base = os.getenv("LITELLM_BASE_URL", "http://litellm:4000/v1")
        openai_key = os.getenv("LITELLM_API_KEY", "")

        await stream(thought(source=self.nam

*[truncated — see source for full prompt]*