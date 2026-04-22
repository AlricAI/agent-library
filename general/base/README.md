# Base

> """Base classes and utilities for prompt strategies.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Base classes and utilities for prompt strategies.

This module provides shared infrastructure for different prompt strategy
implementations including ReWOO, Plan-and-Execute, Reflexion, and Tree of Thoughts.
"""

from __future__ import annotations

import asyncio
import enum
import platform
from abc import ABC, abstractmethod
from datetime import datetime
from logging import Logger
from typing import TYPE_CHECKING, Any, Literal, Optional, TypeVar

import distro
from pydantic import BaseModel, ConfigDict, Field

from forge.agent.execution_context import (
    ExecutionContext,
    SubAgentHandle,
    SubAgentStatus,
    generate_sub_agent_id,
)
from forge.config.ai_directives import AIDirectives
from forge.config.ai_profile import AIProfile
from forge.llm.prompting import ChatPrompt, LanguageModelClassification
from forge.llm.prompting.utils import format_numbered_list
from forge.llm.providers.schema import (
    AssistantChatMessage,
    AssistantFunctionCall,
    CompletionModelFunction,
)
from forge.models.action import ActionProposal
from forge.models.config import SystemConfiguration, UserConfigurable
from forge.models.utils import ModelWithSummary

if TYPE_CHECKING:
    pass


class PromptStrategyType(str, enum.Enum):
    """Available prompt strategy types."""

    ONE_SHOT = "one_shot"
    REWOO = "rewoo"
    PLAN_EXECUTE = "plan_execute"
    REFLEXION = "reflexion"
    TREE_OF_THOUGHTS = "tree_of_thoughts"
    LATS = "lats"  # Language Agent Tree Search (sub-agent based)
    MULTI_AGENT_DEBATE = "multi_agent_debate"  # Multi-agent debate (sub-agent based)


class PlannedStep(BaseModel):
    """A single step in a multi-step plan.

    Used by ReWOO and Plan-and-Execute strategies.
    """

    thought: str = Field(description="Reasoning for this step")
    tool_name: str = Field(description="Name of the tool to call")
    tool_arguments: dict[str, Any] = Field(
        default_factory=dict, description="Arguments for the tool"
    )
    variable_name: str =

*[truncated — see source for full prompt]*