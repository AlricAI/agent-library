# Rewoo

> """ReWOO (Reasoning Without Observation) Prompt Strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""ReWOO (Reasoning Without Observation) Prompt Strategy.

This strategy implements the ReWOO pattern from the paper:
"ReWOO: Decoupling Reasoning from Observations for Efficient Augmented Language Models"
(https://arxiv.org/abs/2305.18323)

Key benefits:
- 5x token efficiency compared to ReAct
- Generates complete plan upfront, then executes all tools
- Robust under tool-failure scenarios
- Enables parallel tool execution

Pattern:
1. PLAN: Generate full reasoning plan with placeholder variables (#E1, #E2, etc.)
2. EXECUTE: Run all tools (potentially in parallel)
3. SYNTHESIZE: Combine tool results with plan to generate final response
"""

from __future__ import annotations

import json
import re
from enum import Enum
from logging import Logger
from typing import Any, Optional

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

from .base import (
    BaseMultiStepPromptStrategy,
    BasePromptStrategyConfiguration,
    PlannedStep,
    WorkerExecution,
)


class ReWOOPhase(str, Enum):
    """Current phase of the ReWOO execution."""

    PLANNING = "planning"
    EXECUTING = "executing"
    SYNTHESIZING = "synthesizing"


class UseCachedActionException(Exception):
    """Raised during EXECUTING phase to signal that cached action should be used.

    ReWOO pre-plans all actions during PLANNING phase, so EXECUTING phase
    should retrieve actions from the cached plan rather than m

*[truncated — see source for full prompt]*