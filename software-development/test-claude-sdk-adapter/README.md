# Test Claude Sdk Adapter

> """Tests for Claude Agent SDK goal-seeking agent adapter.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for Claude Agent SDK goal-seeking agent adapter.

Tests the ClaudeGoalSeekingAgent which wraps the claude-agent-sdk package.
Covers: init, tools, system prompt, goal formation, native tools,
        agent run, factory integration, tool registration, and close.
"""

from __future__ import annotations

from unittest.mock import MagicMock

import pytest

from amplihack.agents.goal_seeking.sdk_adapters.base import (
    AgentResult,
    AgentTool,
    Goal,
    SDKType,
)
from amplihack.agents.goal_seeking.sdk_adapters.claude_sdk import (
    HAS_CLAUDE_SDK,
    ClaudeGoalSeekingAgent,
)


def _make_agent(**overrides):
    """Create a ClaudeGoalSeekingAgent for testing."""
    defaults = {
        "name": "test-agent",
        "instructions": "Test instructions",
        "model": "claude-opus-4-6",
        "enable_memory": False,
    }
    defaults.update(overrides)
    return ClaudeGoalSeekingAgent(**defaults)


# ===========================================================================
# Test Classes
# ===========================================================================


class TestSDKType:
    def test_claude_type_exists(self):
        assert SDKType.CLAUDE == "claude"

    def test_mini_type_exists(self):
        assert SDKType.MINI == "mini"

    def test_copilot_type_exists(self):
        assert SDKType.COPILOT == "copilot"

    def test_microsoft_type_exists(self):
        assert SDKType.MICROSOFT == "microsoft"


class TestAgentTool:
    def test_basic_creation(self):
        t = AgentTool(
            name="test_tool",
            description="A test tool",
            parameters={"type": "object", "properties": {}},
            function=lambda: None,
        )
        assert t.name == "test_tool"
        assert t.category == "core"
        assert t.requires_approval is False

    def test_with_category(self):
        t = AgentTool(
            name="learn",
            description="Learn",
            parameters={},
            function=lambd

*[truncated — see source for full prompt]*