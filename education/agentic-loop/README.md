# Agentic Loop

> from __future__ import annotations

from collections.abc import Callable

"""Main PERCEIVE→REASON→ACT→LEARN loop for goal-seeking agents.

Philosophy:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

from collections.abc import Callable

"""Main PERCEIVE→REASON→ACT→LEARN loop for goal-seeking agents.

Philosophy:
- Single responsibility: Orchestrate agent loop
- LLM-powered reasoning via amplihack.llm
- Clear separation of concerns (perceive, reason, act, learn)
- Stateless execution (state stored in memory)
- Iterative reasoning: plan → search → evaluate → refine → answer
"""

import json
import logging
import os
from dataclasses import dataclass, field
from typing import Any

from amplihack.llm import completion

logger = logging.getLogger(__name__)

# Default LLM model for the agentic loop (override via constructor parameter)
DEFAULT_MODEL = os.environ.get("EVAL_MODEL", "claude-opus-4-6")


@dataclass
class LoopState:
    """State for one iteration of the agentic loop.

    Attributes:
        perception: What the agent observes
        reasoning: Agent's reasoning about the situation
        action: Action decided by the agent
        learning: What the agent learned from the outcome
        outcome: Result of the action
        iteration: Iteration number
    """

    perception: str
    reasoning: str
    action: dict[str, Any]
    learning: str
    outcome: Any
    iteration: int


@dataclass
class RetrievalPlan:
    """Plan for what information to retrieve from memory.

    Attributes:
        search_queries: Targeted queries to run against memory
        reasoning: Why these queries were chosen
    """

    search_queries: list[str] = field(default_factory=list)
    reasoning: str = ""


@dataclass
class ReasoningStep:
    """A single step in the reasoning trace.

    Attributes:
        step_type: Type of step (plan, search, evaluate, refine)
        queries: Search queries generated or executed
        facts_found: Number of new facts found this step
        evaluation: Sufficiency evaluation if applicable
        reasoning: LLM reasoning for this step
    """

    step_type: str  # "plan", "search", "evaluate", "re

*[truncated — see source for full prompt]*