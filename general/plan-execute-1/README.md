# Plan Execute

> """Plan-and-Execute Prompt Strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Plan-and-Execute Prompt Strategy.

This strategy implements the Plan-and-Execute pattern from research including:
- Plan-and-Act: Long-horizon Task Planning (arxiv.org/html/2503.09572v3)
- Plan-and-Solve Prompting (arxiv.org/abs/2305.04091)
- Routine: Enterprise-Grade Planning (arxiv.org/html/2507.14447)

Key benefits:
- Separates planning from execution for better predictability
- Supports replanning on failure
- Better for long-horizon tasks
- 96.3% accuracy reported in Routine paper

Pattern:
1. PLAN: Generate high-level plan with steps
2. EXECUTE: For each step, generate specific action and execute
3. REPLAN: If step fails, regenerate plan from current state
"""

from __future__ import annotations

import json
import re
from enum import Enum
from logging import Logger
from typing import Optional, Union

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
    PlannedStep,
)


class PlanExecutePhase(str, Enum):
    """Current phase of Plan-and-Execute."""

    VARIABLE_EXTRACTION = "variable_extraction"  # PS+ phase
    PLANNING = "planning"
    EXECUTING = "executing"
    REPLANNING = "replanning"


# PS+ (Plan-and-Solve Plus) Data Models
# From the paper: "Plan-and-Solve Prompting" (arxiv.org/abs/2305.04091)


class ExtractedVariable(ModelWithSummary):
    """A variable extracted from the problem statement (PS+ f

*[truncated — see source for full prompt]*