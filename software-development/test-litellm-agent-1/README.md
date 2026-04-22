# Test Litellm Agent

> """Unit tests for LiteLLMAgent wiring and cost tracking.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Unit tests for LiteLLMAgent wiring and cost tracking."""

from __future__ import annotations

from typing import Any
from unittest.mock import MagicMock, patch

import pytest

from opik_optimizer.agents.litellm_agent import LiteLLMAgent
from opik_optimizer.agents.litellm_agent import _sanitize_tool_arguments_for_logging
from opik_optimizer.api_objects import chat_prompt
from tests.unit.fixtures.builders import make_litellm_completion_response
from tests.unit.fixtures import system_message, user_message


@pytest.fixture
def agent() -> LiteLLMAgent:
    """Create LiteLLMAgent for testing."""
    return LiteLLMAgent(project_name="test-project")


@pytest.fixture
def simple_prompt() -> chat_prompt.ChatPrompt:
    """Create a simple chat prompt for testing."""
    return chat_prompt.ChatPrompt(
        name="test-prompt",
        model="gpt-4o",
        messages=[
            system_message("You are a helpful assistant."),
            user_message("{input}"),
        ],
    )


@pytest.fixture
def tool_prompt() -> chat_prompt.ChatPrompt:
    """Create a prompt with tools for testing."""
    return chat_prompt.ChatPrompt(
        name="tool-prompt",
        model="gpt-4o",
        messages=[
            system_message("You can use tools."),
            user_message("{input}"),
        ],
        tools=[
            {
                "type": "function",
                "function": {
                    "name": "get_weather",
                    "description": "Get weather for a location",
                    "parameters": {
                        "type": "object",
                        "properties": {
                            "location": {"type": "string"},
                        },
                    },
                },
            }
        ],
        function_map={
            "get_weather": lambda location: f"Weather in {location}: Sunny",
        },
    )


class TestLiteLLMAgentInitialization:
    """Test LiteLLMAgent initialization."""

    def test_ba

*[truncated — see source for full prompt]*