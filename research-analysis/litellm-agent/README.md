# Litellm Agent

> """
LiteLLM-backed agent implementation with Opik trace metadata and tool support.

This agent is the default execution layer for optimizers: it rende

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
LiteLLM-backed agent implementation with Opik trace metadata and tool support.

This agent is the default execution layer for optimizers: it renders ChatPrompt
messages, calls LiteLLM for completions, and forwards usage/cost metadata to any
owning optimizer for telemetry and budgeting.
"""

from ..api_objects import chat_prompt
from ..core import llm_calls as _llm_calls
from ..utils import throttle as _throttle
from typing import Any
import json
import logging
import os
from opik import opik_context
import litellm
from opik.integrations.litellm import track_completion
from . import optimizable_agent
from ..constants import resolve_project_name
from ..utils.opik_env import set_project_name_env
from ..utils.logging import debug_tool_call
from ..constants import tool_call_max_iterations
from ..utils.candidate_selection import extract_choice_logprob
from ..utils import prompt_tracing
from ..utils.toolcalling.normalize.tool_factory import resolve_toolcalling_tools
from typing import TYPE_CHECKING

if TYPE_CHECKING:
    from litellm.types.utils import Choices, Usage


logger = logging.getLogger(__name__)
_WARNED_NO_LOGPROBS = False
_SENSITIVE_ARGUMENT_KEYS = (
    "key",
    "token",
    "secret",
    "password",
    "passwd",
    "api_key",
)
_MAX_LOG_VALUE_LENGTH = 48


def _sanitize_tool_arguments_for_logging(arguments: Any) -> Any:
    """Return a redacted copy of tool-call arguments for exception logs."""
    if isinstance(arguments, dict):
        sanitized: dict[str, Any] = {}
        for key, value in arguments.items():
            key_text = str(key)
            key_lower = key_text.lower()
            if any(secret in key_lower for secret in _SENSITIVE_ARGUMENT_KEYS):
                sanitized[key_text] = "***REDACTED***"
            else:
                sanitized[key_text] = _sanitize_tool_arguments_for_logging(value)
        return sanitized
    if isinstance(arguments, list):
        return [_sanitize_tool_arguments_for_logging(item) for item in argument

*[truncated — see source for full prompt]*