# Test Database Agent

> """
Integration tests for database-defined agents.

Tests creating and running agents from AgentDefinition records.
"""

import asyncio
import uuid
fr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Integration tests for database-defined agents.

Tests creating and running agents from AgentDefinition records.
"""

import asyncio
import uuid
from unittest.mock import AsyncMock, MagicMock, patch

import pytest

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    ToolStrategy,
    create_agent_from_definition,
)
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
def basic_agent_definition():
    """Create a basic mock AgentDefinition."""
    definition = MagicMock()
    definition.id = uuid.uuid4()
    definition.name = "test-db-agent"
    definition.display_name = "Test DB Agent"
    definition.instructions = "You are a helpful test agent."
    definition.tools = {"names": ["web_search"]}
    definition.model = "agent"
    definition.workflows = None
    definition.scopes = []
    definition.is_active = True
    return definition


@pytest.fixture
def document_agent_definition():
    """Create a document search agent definition."""
    definition = MagicMock()
    definition.id = uuid.uuid4()
    definition.name = "doc-search-agent"
    definition.display_name = "Document Search Agent"
    definition.instructions = "Search documents and answer questions."
    definition.tools = {"names": ["document_search"]}
    definition.model = "agent"
    definition.workflows = {
        "execution_mode": "run_once",
        "tool_strategy": "predefined_

*[truncated — see source for full prompt]*