# Reflexion

> """Reflexion Prompt Strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Reflexion Prompt Strategy.

This strategy implements the Reflexion pattern from research including:
- Reflexion: Verbal Reinforcement Learning (arxiv.org/abs/2303.11366)
- Self-Refine: Iterative Self-Feedback (arxiv.org/abs/2303.17651)
- Self-Reflection in LLM Agents (arxiv.org/abs/2405.06682)

Key benefits:
- 91% pass@1 on HumanEval (vs GPT-4's 80%)
- No training required - same LLM generates, critiques, refines
- Agents store reflections in episodic memory for better future decisions
- Supports 8 types of self-reflection that improve problem-solving

Pattern:
1. GENERATE: Propose action
2. EXECUTE: Run action
3. REFLECT: Critique result, extract lessons
4. RETRY: Use reflection to improve next attempt
"""

from __future__ import annotations

import json
import re
from datetime import datetime
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
    ChatMessage,
    CompletionModelFunction,
)
from forge.models.action import ActionProposal
from forge.models.config import UserConfigurable
from forge.models.json_schema import JSONSchema
from forge.models.utils import ModelWithSummary
from forge.utils.exceptions import InvalidAgentResponseError

from .base import (
    BaseMultiStepPromptStrategy,
    BasePromptStrategyConfiguration,
    Reflection,
    ReflexionMemory,
)


class ReflexionPhase(str, Enum):
    """Current phase of Reflexion execution."""

    PROPOSING = "proposing"
    REFLECTING = "reflecting"


class EvaluatorType(str, Enum):
    """Type of evaluator for determining action success (from Reflexion paper)."""

    LLM = "llm"  # Use LLM to evaluate result
    HEURISTIC = "heuristic"  # Use pattern-

*[truncated — see source for full prompt]*