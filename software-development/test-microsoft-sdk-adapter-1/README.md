# Test Microsoft Sdk Adapter

> """Tests for MicrosoftGoalSeekingAgent (Microsoft Agent Framework adapter).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for MicrosoftGoalSeekingAgent (Microsoft Agent Framework adapter).

Tests cover:
- Initialization and configuration
- Tool mapping and wrapping
- Tool implementations (with and without memory)
- Goal formation
- Full agent run (with mocked SDK)
- Session management
- Factory integration
- Prompt template loading
- Tool wrapping helpers
- Security and input validation
- Base class interface compliance
"""

from __future__ import annotations

import asyncio
import os
from pathlib import Path
from typing import Any
from unittest.mock import AsyncMock, MagicMock, patch

from amplihack.agents.goal_seeking.sdk_adapters.base import (
    AgentResult,
    AgentTool,
    Goal,
    GoalSeekingAgent,
    SDKType,
)
from amplihack.agents.goal_seeking.sdk_adapters.microsoft_sdk import (
    MicrosoftGoalSeekingAgent,
    _build_learning_tools,
    _load_prompt,
    _wrap_tool,
)

_TEST_API_KEY = "test-key-for-unit-tests"  # pragma: allowlist secret

import amplihack.agents.goal_seeking.sdk_adapters.microsoft_sdk as _ms_sdk

# Permanently mock agent-framework at module level since it's not installed.
# This allows all tests to create MicrosoftGoalSeekingAgent instances without
# needing the real agent-framework package.
_MOCK_SESSION = MagicMock()
_MOCK_AF_AGENT_INSTANCE = MagicMock()
_MOCK_AF_AGENT_INSTANCE.create_session.return_value = _MOCK_SESSION
_MOCK_AF_AGENT_CLS = MagicMock(return_value=_MOCK_AF_AGENT_INSTANCE)
_MOCK_AF_FUNCTION_TOOL_CLS = MagicMock()
_MOCK_OPENAI_CLIENT_CLS = MagicMock()

_ms_sdk._HAS_AGENT_FRAMEWORK = True
_ms_sdk.AFAgent = _MOCK_AF_AGENT_CLS
_ms_sdk.AFFunctionTool = _MOCK_AF_FUNCTION_TOOL_CLS
_ms_sdk.OpenAIChatClient = _MOCK_OPENAI_CLIENT_CLS

# Keep backward-compatible aliases used in some tests
_MOCK_AF_AGENT = _MOCK_AF_AGENT_INSTANCE
_MOCK_AF_FUNCTION_TOOL = _MOCK_AF_FUNCTION_TOOL_CLS
_MOCK_OPENAI_CLIENT = _MOCK_OPENAI_CLIENT_CLS


def _make_agent(
    name: str = "test-agent",
    instructions: str = "",
    model: str = "claude-opus-4-6-t

*[truncated — see source for full prompt]*