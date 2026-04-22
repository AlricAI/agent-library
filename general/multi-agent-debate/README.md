# Multi Agent Debate

> """Multi-Agent Debate prompt strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Multi-Agent Debate prompt strategy.

This strategy implements a multi-agent debate approach where multiple sub-agents
propose solutions, debate their merits, and reach a consensus.

Based on research from:
- "Improving Factuality and Reasoning in Language Models through Multiagent Debate"
- Google ADK Multi-Agent Patterns

Key features:
- Multiple sub-agents generate independent proposals
- Agents critique each other's proposals
- Consensus is reached through voting or synthesis
- Improves reasoning through diverse perspectives
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


class DebatePhase(str, Enum):
    """Phases of the multi-agent debate."""

    PROPOSAL = "proposal"  # Agents generate initial proposals
    CRITIQUE = "critique"  # Agents critique each other's proposals
    REVISION = "revision"  # Agents revise based on critiques
    CONSENSUS = "consensus"  # Synthesize final decision
    EXECUTION = "execution"  # Execute the consensus action


class AgentProposal(BaseModel):
    """A proposal from a debate agent."""

    agent_id: str = Field(description="ID of the proposing agent")
    action_name: str = Field(description="Proposed action name")
    action

*[truncated — see source for full prompt]*