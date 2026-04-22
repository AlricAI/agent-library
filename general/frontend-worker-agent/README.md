# Frontend Worker Agent

> """
Frontend Worker Agent for React/TypeScript component generation (Sprint 4: cf-48).

This agent specializes in generating React components with Typ

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Frontend Worker Agent for React/TypeScript component generation (Sprint 4: cf-48).

This agent specializes in generating React components with TypeScript,
following project conventions (Tailwind CSS, functional components).
"""

import json
import logging
import asyncio
from pathlib import Path
from typing import Dict, Any, Optional

from codeframe.adapters.llm.base import Purpose
from codeframe.core.models import Task, AgentMaturity
from codeframe.agents.worker_agent import WorkerAgent

logger = logging.getLogger(__name__)


class FrontendWorkerAgent(WorkerAgent):
    """
    Frontend Worker Agent - Specialized in React/TypeScript component generation.

    Capabilities:
    - Generate functional React components with TypeScript
    - Create TypeScript interfaces for props and state
    - Follow project conventions (Tailwind CSS, functional components)
    - Auto-update imports and exports
    - Integrate with WebSocket broadcasts for real-time status
    """

    def __init__(
        self,
        agent_id: str,
        provider: str = "anthropic",
        maturity: AgentMaturity = AgentMaturity.D1,
        api_key: Optional[str] = None,
        websocket_manager=None,
        db=None,
    ):
        """
        Initialize Frontend Worker Agent.

        Args:
            agent_id: Unique agent identifier
            provider: LLM provider (default: anthropic)
            maturity: Agent maturity level
            api_key: API key for LLM provider (uses ANTHROPIC_API_KEY env var if not provided)
            websocket_manager: WebSocket connection manager for broadcasts
            db: Database instance for blocker management (optional)
        """
        super().__init__(
            agent_id=agent_id,
            agent_type="frontend",
            provider=provider,
            maturity=maturity,
            system_prompt=self._build_system_prompt(),
            db=db,
        )
        # api_key kept for backwards compatibility; LLM calls use self.llm_prov

*[truncated — see source for full prompt]*