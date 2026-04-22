# Tool

> from string import Template
from typing import List, NamedTuple, Optional, Union

from langchain.tools import BaseTool
from pydantic import Field


fr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from string import Template
from typing import List, NamedTuple, Optional, Union

from langchain.tools import BaseTool
from pydantic import Field


from agentverse.memory import BaseMemory, ChatHistoryMemory
from agentverse.message import Message
from agentverse.utils import AgentAction, AgentFinish
from agentverse.logging import logger

# from . import agent_registry
# from .base import BaseAgent

from agentverse.agents import agent_registry
from agentverse.agents.base import BaseAgent


class ToolNotExistError(BaseException):
    """Exception raised when parsing output from a command fails."""

    def __init__(self, tool_name=""):
        self.tool_name = tool_name

    def __str__(self):
        return f"Tool {self.tool_name} does not exist."


@agent_registry.register("tool")
class ToolAgent(BaseAgent):
    tools: List[BaseTool] = Field(default=[])
    tool_memory: BaseMemory = Field(default_factory=ChatHistoryMemory)
    verbose: bool = Field(default=False)

    def step(self, env_description: str = "") -> Message:
        parsed_response = None
        tool_observation = [self.tool_memory.to_string()]
        while True:
            prompt = self._fill_prompt_template(env_description, tool_observation)

            for i in range(self.max_retry):
                try:
                    response = self.llm.generate_response(prompt)
                    parsed_response = self.output_parser.parse(response)
                    if isinstance(parsed_response, AgentAction):
                        observation = self._call_tool(parsed_response)
                        tool_observation.append(
                            parsed_response.log.strip()
                            + f"\nObservation: {observation.strip()}"
                        )
                    break
                except BaseException as e:
                    logger.error(e)
                    logger.warn("Retrying...")
                    continue
            if parsed_response is None or isinst

*[truncated — see source for full prompt]*