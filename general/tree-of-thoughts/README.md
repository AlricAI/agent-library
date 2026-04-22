# Tree Of Thoughts

> """Tree of Thoughts (ToT) Prompt Strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tree of Thoughts (ToT) Prompt Strategy.

This strategy implements the Tree of Thoughts pattern from research including:
- Tree of Thoughts: Deliberate Problem Solving (arxiv.org/abs/2305.10601)
- ToTRL: Unlock Tree-of-Thought via Puzzles (arxiv.org/abs/2505.12717)
- Tree of Uncertain Thoughts (arxiv.org/abs/2309.07694)

Key benefits:
- Frames problem solving as search over a tree of partial solutions
- Enables backtracking when a reasoning path fails
- Self-evaluates choices to decide next action
- Better for complex reasoning and exploration tasks

Pattern:
1. GENERATE: Multiple candidate thoughts at each step
2. EVALUATE: Score each thought (1-10)
3. SEARCH: BFS/DFS through the thought tree
4. BACKTRACK: If dead end, try alternative paths
"""

from __future__ import annotations

import json
import re
from collections import Counter
from enum import Enum
from logging import Logger
from typing import Any, Literal, Optional

from pydantic import Field

from forge.config.ai_directives import AIDirectives
from forge.config.ai_profile import AIProfile
from forge.json.parsing import extract_dict_from_json
from forge.llm.prompting import ChatPrompt, LanguageModelClassification
from forge.llm.providers.schema import (
    AssistantChatMessage,
    AssistantFunctionCall,
    ChatMessage,
    CompletionModelFunction,
)
from forge.models.action import ActionProposal
from forge.models.config import UserConfigurable
from forge.models.json_schema import JSONSchema
from forge.models.utils import ModelWithSummary
from forge.utils.exceptions import InvalidAgentResponseError

from .base import BaseMultiStepPromptStrategy, BasePromptStrategyConfiguration, Thought


class ToTPhase(str, Enum):
    """Current phase of Tree of Thoughts execution."""

    GENERATING = "generating"
    EVALUATING = "evaluating"
    SELECTING = "selecting"


class ToTThoughts(ModelWithSummary):
    """Thoughts model for Tree of Thoughts strategy."""

    current_path: list[str] = Field(
        default_f

*[truncated — see source for full prompt]*