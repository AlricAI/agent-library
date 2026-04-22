# Lats

> """LATS (Language Agent Tree Search) prompt strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""LATS (Language Agent Tree Search) prompt strategy.

This strategy implements the LATS algorithm from the paper:
"Language Agent Tree Search Unifies Reasoning Acting and Planning in Language Models"

LATS uses sub-agents to explore different reasoning paths with Monte Carlo Tree Search,
combining the benefits of tree search with LLM-based evaluation.

Key features:
- Sub-agents explore different action paths in parallel
- Monte Carlo Tree Search for intelligent exploration
- Value function learned from sub-agent outcomes
- Reflection on failed paths to improve future exploration
"""

from __future__ import annotations

import json
import re
from enum import Enum
from logging import Logger
from typing import Any, Optional

from pydantic import BaseModel, Field

from forge.config.ai_directives import AIDirectives
from forge.config.ai_profile import AIProfile
from forge.json.parsing import extract_dict_from_json
from forge.llm.prompting import ChatPrompt, LanguageModelClassification
from forge.llm.providers.schema import (
    AssistantChatMessage,
    ChatMessage,
    CompletionModelFunction,
)
from forge.models.action import ActionProposal
from forge.models.config import UserConfigurable
from forge.models.json_schema import JSONSchema
from forge.models.utils import ModelWithSummary
from forge.utils.exceptions import InvalidAgentResponseError

from .base import BaseMultiStepPromptStrategy, BasePromptStrategyConfiguration


class LATSPhase(str, Enum):
    """Phases of the LATS algorithm."""

    SELECTION = "selection"  # Select node to expand using UCT
    EXPANSION = "expansion"  # Generate candidate actions via sub-agents
    EVALUATION = "evaluation"  # Evaluate candidates
    BACKPROPAGATION = "backpropagation"  # Update value estimates
    EXECUTION = "execution"  # Execute best action


class LATSNode(BaseModel):
    """A node in the LATS search tree."""

    state_description: str = Field(description="Description of the state at this node")
    action_taken: 

*[truncated — see source for full prompt]*