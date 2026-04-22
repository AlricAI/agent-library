# Critic

> from __future__ import annotations

import json
from colorama import Fore
from agentverse.logging import get_logger
import bdb
from string impor

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

import json
from colorama import Fore
from agentverse.logging import get_logger
import bdb
from string import Template
from typing import TYPE_CHECKING, List, Union

from agentverse.message import Message

from agentverse.agents import agent_registry
from agentverse.agents.base import BaseAgent
from agentverse.utils import AgentCriticism
from agentverse.message import CriticMessage

logger = get_logger()


@agent_registry.register("critic")
class CriticAgent(BaseAgent):
    max_history: int = 3
    tools: List[dict] = []
    tool_names: List[str] = []
    tool_descriptions: str = ""

    def __init__(self, *args, **kwargs):
        tool_config_file = kwargs.pop("tool_config", "")
        tools = []
        tool_names = []
        tool_descriptions = ""
        if tool_config_file != "":
            try:
                with open(tool_config_file, "r") as f:
                    tools_dict = json.load(f)
                tools = tools_dict["tools_json"]
                tool_names = [t["name"] for t in tools]
                tool_descriptions = "\n".join(
                    [f"- {t['name']}: " + t["description"] for t in tools]
                )
                kwargs.update({"tools": tools})
                kwargs.update({"tool_names": tool_names})
                kwargs.update({"tool_descriptions": tool_descriptions})
            except Exception as e:
                logger.error(e)
                logger.warn("Failed to load tool config file.")
        super().__init__(
            *args,
            **kwargs,
        )

    def step(self, env_description: str = "") -> CriticMessage:
        pass

    async def astep(
        self,
        preliminary_solution: str,
        advice: str = "No advice yet.",
        task_description: str = "",
        all_roles: str = "",
        **kwargs,
    ) -> CriticMessage:
        """Asynchronous version of step"""
        logger.

*[truncated — see source for full prompt]*