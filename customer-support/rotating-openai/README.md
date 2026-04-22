# Rotating Openai

> """OpenAI provider with automatic API key rotation support.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""OpenAI provider with automatic API key rotation support."""

import logging
import re
from dataclasses import dataclass
from datetime import datetime
from typing import Any

from amplihack.vendor.blarify.agents.api_key_manager import APIKeyManager
from amplihack.vendor.blarify.agents.rotating_provider.rotating_providers import ErrorType, RotatingProviderBase
from langchain_openai import ChatOpenAI
from pydantic import SecretStr

logger = logging.getLogger(__name__)


@dataclass
class OpenAIRotationConfig:
    """Configuration specific to OpenAI rotation."""

    proactive_rotation_threshold_requests: int = 1
    proactive_rotation_threshold_tokens: int = 100
    default_cooldown_seconds: int = 60
    respect_retry_after: bool = True


class RotatingKeyChatOpenAI(RotatingProviderBase):
    """OpenAI chat model with automatic key rotation."""

    def __init__(
        self,
        key_manager: APIKeyManager,
        rotation_config: OpenAIRotationConfig | None = None,
        **kwargs: Any,
    ) -> None:
        """Initialize OpenAI wrapper with rotation support.

        Args:
            key_manager: Manager for API keys
            rotation_config: OpenAI-specific rotation configuration
            **kwargs: Additional arguments for ChatOpenAI
        """
        super().__init__(key_manager, **kwargs)
        self.rotation_config = rotation_config or OpenAIRotationConfig()
        # Remove api_key from kwargs if present (we'll set it per request)
        self.model_kwargs = {k: v for k, v in kwargs.items() if k != "api_key"}

    def _create_client(self, api_key: str) -> ChatOpenAI:
        """Create ChatOpenAI instance with specific API key.

        Args:
            api_key: The API key to use

        Returns:
            ChatOpenAI instance configured with the API key
        """
        return ChatOpenAI(api_key=SecretStr(api_key), **self.model_kwargs)

    def get_provider_name(self) -> str:
        """Return provider name for logging.

        Return

*[truncated — see source for full prompt]*