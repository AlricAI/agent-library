# One Shot

> from __future__ import annotations

import json
import platform
import re
from logging import Logger

import distro
from pydantic import Field

from f

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

import json
import platform
import re
from logging import Logger

import distro
from pydantic import Field

from forge.config.ai_directives import AIDirectives
from forge.config.ai_profile import AIProfile
from forge.json.parsing import extract_dict_from_json
from forge.llm.prompting import ChatPrompt, LanguageModelClassification, PromptStrategy
from forge.llm.prompting.utils import format_numbered_list
from forge.llm.providers.schema import (
    AssistantChatMessage,
    ChatMessage,
    CompletionModelFunction,
)
from forge.models.action import ActionProposal
from forge.models.config import SystemConfiguration, UserConfigurable
from forge.models.json_schema import JSONSchema
from forge.models.utils import ModelWithSummary
from forge.utils.exceptions import InvalidAgentResponseError

_RESPONSE_INTERFACE_NAME = "AssistantResponse"


class AssistantThoughts(ModelWithSummary):
    observations: str = Field(
        description="Relevant observations from your last action (if any)"
    )
    reasoning: str = Field(description="Reasoning behind choosing this action")
    self_criticism: str = Field(description="Constructive self-criticism")
    plan: list[str] = Field(description="Short list that conveys the long-term plan")

    def summary(self) -> str:
        return self.reasoning


class OneShotAgentActionProposal(ActionProposal):
    thoughts: AssistantThoughts  # type: ignore


class OneShotAgentPromptConfiguration(SystemConfiguration):
    DEFAULT_BODY_TEMPLATE: str = (
        "## Constraints\n"
        "You operate within the following constraints:\n"
        "{constraints}\n"
        "\n"
        "## Resources\n"
        "You can leverage access to the following resources:\n"
        "{resources}\n"
        "\n"
        "## Commands\n"
        "These are the ONLY commands you can use."
        " Any action you perform must be possible through one of these commands:\n"
        "{commands}\n"
        "\n"
        "## Best pr

*[truncated — see source for full prompt]*