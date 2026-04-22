# Prisoner Dilemma

> from __future__ import annotations

from string import Template
from typing import TYPE_CHECKING, List

from agentverse.message import Message
from ag

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

from string import Template
from typing import TYPE_CHECKING, List

from agentverse.message import Message
from agentverse.logging import logger

# from . import agent_registry
# from .base import BaseAgent
from agentverse.agents import agent_registry
from agentverse.agents.base import BaseAgent

if TYPE_CHECKING:
    from agentverse.environments.base import BaseEnvironment


class PrisonerDilemaAgent(BaseAgent):
    def step(
        self,
        environment: BaseEnvironment,
        env_description: str = "",
    ) -> Message:
        prompt = self._fill_prompt_template(env_description)

        parsed_response = None
        for i in range(self.max_retry):
            try:
                response = self.llm.generate_response(prompt)
                parsed_response = self.output_parser.parse(self, environment, response)
                break
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

    async def astep(
        self, environment: BaseEnvironment, env_description: str = ""
    ) -> Message:
        """Asynchronous version of step"""
        prompt = self._fill_prompt_template(env_description)

        parsed_response = None
        for i in range(self.max_retry):
            try:
                response = await self.llm.agenerate_response(prompt)
                parsed_response = self.output_parser.parse(self, environment, response)
                break
            except Exception as e:
                logger.error(e)
                logger.warn("Retrying...")
             

*[truncated — see source for full prompt]*