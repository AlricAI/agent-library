# Coach Agent

> """
Coach Agent.

Provides real-time text-based coaching and suggestions
to the human user during their conversation.
"""

import asyncio
import loggi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Coach Agent.

Provides real-time text-based coaching and suggestions
to the human user during their conversation.
"""

import asyncio
import logging
from dataclasses import dataclass, field
from datetime import datetime
from typing import Any, Dict, List, Optional

import httpx
import structlog

from config.settings import get_settings

logger = structlog.get_logger(__name__)


@dataclass
class CoachSuggestion:
    """A coaching suggestion."""

    text: str
    category: str  # "info", "question", "warning", "action"
    confidence: float
    timestamp: datetime = field(default_factory=datetime.utcnow)


@dataclass
class CoachContext:
    """Context for the coaching session."""

    call_purpose: Optional[str] = None
    key_topics: List[str] = field(default_factory=list)
    user_goals: List[str] = field(default_factory=list)
    important_info: Dict[str, str] = field(default_factory=dict)


class CoachAgent:
    """
    AI coaching agent for assisting humans during calls.
    
    Provides:
    - Suggested questions to ask
    - Information reminders
    - Warnings about common issues
    - Action suggestions based on conversation
    """

    def __init__(
        self,
        context: Optional[CoachContext] = None,
    ):
        settings = get_settings()
        
        self._context = context or CoachContext()
        
        self._litellm_url = settings.litellm_base_url
        self._litellm_key = settings.litellm_api_key
        self._model = settings.default_model
        
        self._transcript_history: List[Dict] = []
        self._suggestions_given: List[CoachSuggestion] = []
        self._is_active = False

    def start(self) -> None:
        """Start the coaching session."""
        self._is_active = True
        logger.info("Coach agent started")

    def stop(self) -> None:
        """Stop the coaching session."""
        self._is_active = False
        logger.info("Coach agent stopped")

    async def process_transcript(
        self,
   

*[truncated — see source for full prompt]*