# Worker Agent

> """Worker Agent implementation for CodeFRAME.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Worker Agent implementation for CodeFRAME."""

import os
import logging
import asyncio
from datetime import datetime, timedelta, timezone
from typing import Optional, List, Dict, Any, TYPE_CHECKING
from collections import deque

if TYPE_CHECKING:
    from codeframe.enforcement.evidence_verifier import Evidence

from tenacity import (
    retry,
    stop_after_attempt,
    wait_exponential,
    retry_if_exception_type,
)

from codeframe.adapters.llm.base import (
    LLMProvider,
    LLMAuthError,
    LLMRateLimitError,
    LLMConnectionError,
)
from codeframe.adapters.llm import get_provider

from codeframe.core.models import (
    Task, TaskStatus, AgentMaturity, ContextItemType, ContextTier, CallType
)
from codeframe.enforcement.quality_tracker import QualityTracker, QualityMetrics

logger = logging.getLogger(__name__)

# Supported Claude models for execute_task (stable aliases — no date suffixes)
SUPPORTED_MODELS = [
    "claude-haiku-4-5",
    "claude-sonnet-4-5",
    "claude-opus-4-5",
    "claude-opus-4",
]

# Model pricing (USD per million tokens) - as of 2026-04
MODEL_PRICING = {
    "claude-haiku-4-5": {"input": 0.0000008, "output": 0.000004},
    "claude-sonnet-4-5": {"input": 0.000003, "output": 0.000015},
    "claude-opus-4-5": {"input": 0.000015, "output": 0.000075},
    "claude-opus-4": {"input": 0.000015, "output": 0.000075},
}


class WorkerAgent:
    """
    Worker Agent - Specialized agent for specific tasks (Backend, Frontend, Test, Review).
    """

    def __init__(
        self,
        agent_id: str,
        agent_type: str,
        provider: str,
        maturity: AgentMaturity = AgentMaturity.D1,
        system_prompt: str | None = None,
        db: Optional[Any] = None,
        model_name: str = "claude-sonnet-4-5",
        llm_provider: Optional[LLMProvider] = None,
    ):
        """Initialize Worker Agent.

        Args:
            agent_id: Unique agent identifier
            agent_type: Type of agent (backend, frontend, test, revie

*[truncated — see source for full prompt]*