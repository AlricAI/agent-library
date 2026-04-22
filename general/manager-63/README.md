# Manager

> from __future__ import annotations

import asyncio
from colorama import Fore

from agentverse.logging import get_logger
import bdb
from string import 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

import asyncio
from colorama import Fore

from agentverse.logging import get_logger
import bdb
from string import Template
from typing import TYPE_CHECKING, List, Tuple

from agentverse.message import Message

from agentverse.agents import agent_registry
from agentverse.agents.base import BaseAgent
from agentverse.utils import AgentCriticism

import random
from rapidfuzz import fuzz


logger = get_logger()


@agent_registry.register("manager")
class ManagerAgent(BaseAgent):
    prompt_template: str

    def step(
        self,
        former_solution: str,
        candidate_critic_opinions: List[AgentCriticism],
        advice: str,
        task_description: str = "",
        previous_sentence: str = "",
    ) -> Message:
        logger.debug("", self.name, Fore.MAGENTA)

        prompt = self._fill_prompt_template(
            former_solution,
            candidate_critic_opinions,
            advice,
            task_description,
            previous_sentence,
        )

        logger.debug(f"Prompt:\n{prompt}", "Manager", Fore.CYAN)
        parsed_response = None
        for i in range(self.max_retry):
            try:
                # LLM Manager
                # response = self.llm.generate_response(prompt)
                # parsed_response = self.output_parser.parse(response)
                selected_role_description = self.llm.generate_response(prompt).content
                candidate_score_list = [
                    fuzz.ratio(candidate.sender, selected_role_description)
                    for candidate in candidate_critic_opinions
                ]
                selected_index = candidate_score_list.index(max(candidate_score_list))
                candidate_critic_opinion = candidate_critic_opinions[selected_index]

                # Random Manager
                # parsed_response = random.choice(candidate_critic_opinions)
                break
            except (KeyboardInterrupt, bdb.BdbQuit):
               

*[truncated — see source for full prompt]*