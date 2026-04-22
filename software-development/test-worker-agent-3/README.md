# Test Worker Agent

> """
Test Worker Agent for pytest test generation (Sprint 4: cf-49).

This agent specializes in generating pytest test cases,
analyzing code for test r

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Test Worker Agent for pytest test generation (Sprint 4: cf-49).

This agent specializes in generating pytest test cases,
analyzing code for test requirements, and self-correcting failing tests.
"""

import sys
import json
import logging
import asyncio
import subprocess
import re
from pathlib import Path
from typing import Dict, Any, Optional, Tuple

from codeframe.adapters.llm.base import Purpose
from codeframe.core.models import Task, AgentMaturity
from codeframe.agents.worker_agent import WorkerAgent

logger = logging.getLogger(__name__)


class TestWorkerAgent(WorkerAgent):
    """
    Test Worker Agent - Specialized in pytest test generation and validation.

    Capabilities:
    - Generate pytest test cases for Python code
    - Analyze target code to understand test requirements
    - Execute generated tests and validate results
    - Self-correct failing tests (up to 3 attempts)
    - Follow pytest conventions (fixtures, parametrize, mocks)
    - Integrate with WebSocket broadcasts for test results
    """

    __test__ = False  # Not a test class - it's an agent that generates tests

    def __init__(
        self,
        agent_id: str,
        provider: str = "anthropic",
        maturity: AgentMaturity = AgentMaturity.D1,
        api_key: Optional[str] = None,
        websocket_manager=None,
        max_correction_attempts: int = 3,
        db=None,
    ):
        """
        Initialize Test Worker Agent.

        Args:
            agent_id: Unique agent identifier
            provider: LLM provider (default: anthropic)
            maturity: Agent maturity level
            api_key: API key for LLM provider
            websocket_manager: WebSocket connection manager
            max_correction_attempts: Maximum self-correction attempts
            db: Database instance for blocker management (optional)
        """
        super().__init__(
            agent_id=agent_id,
            agent_type="test",
            provider=provider,
            maturity=

*[truncated — see source for full prompt]*