# Conversation

> from __future__ import annotations
from colorama import Fore


from agentverse.logging import get_logger
import bdb
from string import Template
from t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations
from colorama import Fore

# import logging
from agentverse.logging import get_logger
import bdb
from string import Template
from typing import TYPE_CHECKING, List

from agentverse.message import Message

# from . import agent_registry
# from .base import BaseAgent
from agentverse.agents import agent_registry
from agentverse.agents.base import BaseAgent

logger = get_logger()


@agent_registry.register("conversation")
class ConversationAgent(BaseAgent):
    def step(self, env_description: str = "") -> Message:
        prompt = self._fill_prompt_template(env_description)

        parsed_response = None
        for i in range(self.max_retry):
            try:
                response = self.llm.generate_response(prompt)
                parsed_response = self.output_parser.parse(response)
                break
            except KeyboardInterrupt:
                raise
            except Exception as e:
                logger.error(e)
                logger.warn("Retrying...")
                continue

        if parsed_response is None:
            logger.error(f"{self.name} failed to generate valid response.")

        message = Message(
            content=""
            if parsed_response is None
            else parsed_response.return_values["output"],
            sender=self.name,
            receiver=self.get_receiver(),
        )
        return message

    async def astep(self, env_description: str = "") -> Message:
        """Asynchronous version of step"""
        prompt = self._fill_prompt_template(env_description)

        parsed_response = None
        for i in range(self.max_retry):
            try:
                # if self.name == "Code Reviewer":
                logger.debug(prompt, "Prompt", Fore.CYAN)
                response = await self.llm.agenerate_response(prompt)

                # logging.info(f"{self.name}'s request result:"
                #              f" {response.content}")
                parsed_respo

*[truncated — see source for full prompt]*