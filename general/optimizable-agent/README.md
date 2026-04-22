# Optimizable Agent

> """Agent interface used by optimizers to invoke LLM prompts and score outputs.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Agent interface used by optimizers to invoke LLM prompts and score outputs."""

from abc import ABC
from typing import Any, TYPE_CHECKING
import json
import copy

import litellm
from litellm.integrations.opik.opik import OpikLogger
from opik import opik_context
from opik.integrations.litellm import track_completion
from ..constants import resolve_project_name, tool_call_max_iterations
from ..utils.opik_env import set_project_name_env
from ..utils import throttle as _throttle
from ..utils.logging import debug_tool_call
from ..utils.toolcalling.normalize.tool_factory import resolve_toolcalling_tools
from ..utils import prompt_tracing

_limiter = _throttle.get_rate_limiter_for_current_opik_installation()

if TYPE_CHECKING:
    from ..api_objects import chat_prompt

# FIXME: This class inherits from ABC but provides concrete implementations.
# Consider splitting into OptimizableAgentInterface (ABC) and DefaultOptimizableAgent (concrete)
# or removing ABC inheritance if we want to keep it as a concrete base class.


# TODO: Verify if this function is still used anywhere, remove if unused
def tools_to_dict(tools: dict[str, dict[str, Any]]) -> dict[str, Any]:
    """Convert tools dictionary to a simplified format."""
    retval = {}
    for name in tools:
        parts = {}
        for part in tools[name]:
            if isinstance(tools[name][part], (int, float, str)):
                parts[part] = tools[name][part]
        if parts:
            retval[name] = parts
    return retval


class OptimizableAgent(ABC):
    """
    Base agent interface for optimizer-driven prompt evaluation.

    Implementations should translate prompt templates + dataset items into model
    calls, and return outputs suitable for scoring. Optimizers may request either
    a single response (invoke_agent) or a list of candidates for pass@k selection
    (invoke_agent_candidates).

    This class can be used as an abstract interface (for type checking and subclassing)
    or as a concrete imp

*[truncated — see source for full prompt]*