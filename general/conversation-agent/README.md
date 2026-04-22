# Conversation Agent

> """
Conversation Agent.

Handles real-time voice conversations with the remote party
using local LLM for responses and TTS for speech synthesis.
"""



## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Conversation Agent.

Handles real-time voice conversations with the remote party
using local LLM for responses and TTS for speech synthesis.
"""

import asyncio
import logging
from dataclasses import dataclass, field
from datetime import datetime
from enum import Enum
from typing import Any, Callable, Dict, List, Optional

import httpx
import structlog

from config.settings import get_settings

logger = structlog.get_logger(__name__)


class ConversationState(str, Enum):
    """Conversation states."""

    IDLE = "idle"
    LISTENING = "listening"
    THINKING = "thinking"
    SPEAKING = "speaking"
    PAUSED = "paused"


@dataclass
class ConversationTurn:
    """Represents a single turn in the conversation."""

    speaker: str  # "ai" or "remote"
    text: str
    timestamp: datetime = field(default_factory=datetime.utcnow)
    audio_duration_ms: Optional[int] = None


@dataclass
class ConversationContext:
    """Context for the conversation."""

    user_name: Optional[str] = None
    target_name: Optional[str] = None
    goal: Optional[str] = None
    key_information: Dict[str, str] = field(default_factory=dict)
    special_instructions: Optional[str] = None


class ConversationAgent:
    """
    AI agent for voice conversations.
    
    Handles:
    - Turn-based conversation flow
    - Context management
    - Response generation via LLM
    - Conversation history
    """

    def __init__(
        self,
        context: Optional[ConversationContext] = None,
        on_response_ready: Optional[Callable[[str], None]] = None,
    ):
        settings = get_settings()
        
        self._context = context or ConversationContext()
        self._on_response_ready = on_response_ready
        
        self._litellm_url = settings.litellm_base_url
        self._litellm_key = settings.litellm_api_key
        self._model = settings.default_model
        
        self._state = ConversationState.IDLE
        self._history: List[ConversationTurn] = []
        self._i

*[truncated — see source for full prompt]*