# Rotating Anthropic

> """Anthropic provider with rotating API key support.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Anthropic provider with rotating API key support."""

import logging
import os
from datetime import datetime
from typing import Any

from amplihack.vendor.blarify.agents.api_key_manager import APIKeyManager

try:
    if os.environ.get("ANTHROPIC_DISABLED", "").lower() == "true":
        raise ImportError("Anthropic disabled via ANTHROPIC_DISABLED=true")
    from langchain_anthropic import ChatAnthropic  # type: ignore[import-untyped]
    from pydantic import SecretStr

    _HAS_LANGCHAIN_ANTHROPIC = True
except ImportError:
    ChatAnthropic = None  # type: ignore[assignment,misc]
    SecretStr = None  # type: ignore[assignment,misc]
    _HAS_LANGCHAIN_ANTHROPIC = False

from .rotating_providers import ErrorType, RotatingProviderBase

logger = logging.getLogger(__name__)


class RotatingKeyChatAnthropic(RotatingProviderBase):
    """Anthropic chat model with automatic key rotation."""

    def __init__(self, key_manager: APIKeyManager, **kwargs: Any) -> None:
        """Initialize the rotating Anthropic provider.

        Args:
            key_manager: The API key manager instance
            **kwargs: Additional ChatAnthropic arguments

        Raises:
            ImportError: If langchain_anthropic is unavailable or Anthropic is disabled.
        """
        if not _HAS_LANGCHAIN_ANTHROPIC:
            raise ImportError(
                "langchain_anthropic is not available or Anthropic is disabled "
                "(ANTHROPIC_DISABLED=true). Cannot instantiate RotatingKeyChatAnthropic."
            )
        super().__init__(key_manager, **kwargs)
        self.model_kwargs = {k: v for k, v in kwargs.items() if k != "api_key"}

    def _create_client(self, api_key: str) -> ChatAnthropic:
        """Create ChatAnthropic instance with specific API key.

        Args:
            api_key: The API key to use

        Returns:
            ChatAnthropic instance configured with the key
        """
        return ChatAnthropic(api_key=SecretStr(api_key), **self.model

*[truncated — see source for full prompt]*