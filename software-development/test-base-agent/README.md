# Test Base Agent

> """
Unit tests for BaseStreamingAgent framework.

Tests cover:
- AgentConfig validation and defaults
- ExecutionMode behavior
- ToolStrategy execution

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Unit tests for BaseStreamingAgent framework.

Tests cover:
- AgentConfig validation and defaults
- ExecutionMode behavior
- ToolStrategy execution patterns
- Authentication and token exchange
- Tool execution with streaming events
- Synthesis and fallback handling
- Pipeline execution
"""

import asyncio
from dataclasses import dataclass
from typing import Any, Dict, List, Optional
from unittest.mock import AsyncMock, MagicMock, patch

import pytest

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    ToolRegistry,
    ToolStrategy,
    TOOL_SCOPES,
    create_agent_from_definition,
)
from app.schemas.auth import Principal
from app.schemas.streaming import StreamEvent


# =============================================================================
# Test Fixtures
# =============================================================================


@pytest.fixture
def mock_stream_callback():
    """Create a mock streaming callback that collects events."""
    events = []
    
    async def callback(event: StreamEvent):
        events.append(event)
    
    callback.events = events
    return callback


@pytest.fixture
def mock_cancel_event():
    """Create a mock cancellation event."""
    return asyncio.Event()


@pytest.fixture
def test_principal():
    """Create a test principal with token."""
    return Principal(
        sub="test-user-123",
        email="test@example.com",
        roles=["user"],
        scopes=["search.read", "data.write"],
        token="test-jwt-token-12345",
    )


@pytest.fixture
def test_agent_config():
    """Create a basic test AgentConfig."""
    return AgentConfig(
        name="test-agent",
        display_name="Test Agent",
        instructions="You are a test agent. Be helpful.",
        tools=["document_search"],
        execution_mode=ExecutionMode.RUN_ONCE,
        tool_strategy=ToolStrategy.PREDEFINED_PIPELINE,
    )


@pytest.fixture
def tes

*[truncated — see source for full prompt]*