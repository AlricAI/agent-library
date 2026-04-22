# Base Agent Executor Mixin

> import time
from typing import TYPE_CHECKING, Dict, List

from crewai.memory.entity.entity_memory_item import EntityMemoryItem
from crewai.memory.long

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import time
from typing import TYPE_CHECKING, Dict, List

from crewai.memory.entity.entity_memory_item import EntityMemoryItem
from crewai.memory.long_term.long_term_memory_item import LongTermMemoryItem
from crewai.utilities import I18N
from crewai.utilities.converter import ConverterError
from crewai.utilities.evaluators.task_evaluator import TaskEvaluator
from crewai.utilities.printer import Printer
from crewai.utilities.events.event_listener import event_listener

if TYPE_CHECKING:
    from crewai.agents.agent_builder.base_agent import BaseAgent
    from crewai.crew import Crew
    from crewai.task import Task


class CrewAgentExecutorMixin:
    crew: "Crew"
    agent: "BaseAgent"
    task: "Task"
    iterations: int
    max_iter: int
    messages: List[Dict[str, str]]
    _i18n: I18N
    _printer: Printer = Printer()

    def _create_short_term_memory(self, output) -> None:
        """Create and save a short-term memory item if conditions are met."""
        if (
            self.crew
            and self.agent
            and self.task
            and "Action: Delegate work to coworker" not in output.text
        ):
            try:
                if (
                    hasattr(self.crew, "_short_term_memory")
                    and self.crew._short_term_memory
                ):
                    self.crew._short_term_memory.save(
                        value=output.text,
                        metadata={
                            "observation": self.task.description,
                        },
                        agent=self.agent.role,
                    )
            except Exception as e:
                print(f"Failed to add to short term memory: {e}")
                pass

    def _create_external_memory(self, output) -> None:
        """Create and save a external-term memory item if conditions are met."""
        if (
            self.crew
            and self.agent
            and self.task
            and hasattr(self.crew, "_external_m

*[truncated — see source for full prompt]*