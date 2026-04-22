# Test Copilot Sdk Adapter

> """Tests for the GitHub Copilot SDK goal-seeking agent adapter.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for the GitHub Copilot SDK goal-seeking agent adapter.

37 tests across 8 test classes covering:
- TestCopilotGoalSeekingAgent: init, config, env vars, tools, defaults
- TestToolConversion: AgentTool -> CopilotTool mapping
- TestResponseExtraction: SessionEvent content parsing
- TestAgentRun: success, timeout, error, lifecycle
- TestSessionLifecycle: create, idempotent, stop, force_stop, context manager
- TestToolRegistration: dynamic registration, session invalidation
- TestFactory: factory creates copilot, default is copilot
- TestSecurityAudit: no eval, bounded timeout, generic errors
"""

from __future__ import annotations

import asyncio
import os
from types import SimpleNamespace
from unittest.mock import AsyncMock, MagicMock, patch

import pytest

_P = "amplihack.agents.goal_seeking.sdk_adapters.copilot_sdk"


# ---------------------------------------------------------------------------
# Helpers
# ---------------------------------------------------------------------------
def _make_agent(**overrides):
    """Create a CopilotGoalSeekingAgent with mocked SDK and memory."""
    defaults = {
        "name": "test-agent",
        "instructions": "Test instructions",
        "model": "claude-opus-4-6",
        "enable_memory": False,
        "enable_eval": False,
    }
    defaults.update(overrides)

    with patch(f"{_P}.HAS_COPILOT_SDK", True):
        from amplihack.agents.goal_seeking.sdk_adapters.copilot_sdk import (
            CopilotGoalSeekingAgent,
        )

        return CopilotGoalSeekingAgent(**defaults)


def _make_event(content="Hello"):
    """Create a mock SessionEvent with data.content."""
    return SimpleNamespace(
        type="assistant.message",
        data=SimpleNamespace(content=content),
    )


def _tool_result_attr(result, old_name: str, new_name: str):
    if hasattr(result, new_name):
        return getattr(result, new_name)
    return result[old_name]


def _client_option_env(options):
    if hasattr(options, "env"):
    

*[truncated — see source for full prompt]*