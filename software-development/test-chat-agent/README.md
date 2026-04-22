# Test Chat Agent

> """
Integration tests for ChatAgent with authentication.

Tests the chat agent's ability to use all its tools:
- get_weather: Weather queries
- web_se

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Integration tests for ChatAgent with authentication.

Tests the chat agent's ability to use all its tools:
- get_weather: Weather queries
- web_search: Web research queries  
- document_search: Document queries (requires auth)
"""

import asyncio
from typing import List
from unittest.mock import AsyncMock, MagicMock, patch

import pytest

from app.agents.chat_agent import chat_agent, ChatAgent
from app.agents.base_agent import BaseStreamingAgent, AgentContext, ToolRegistry
from app.schemas.auth import Principal
from app.schemas.streaming import StreamEvent


# =============================================================================
# Test Fixtures
# =============================================================================


@pytest.fixture
def mock_stream_callback():
    """Create a mock stream callback that collects events."""
    class StreamCollector:
        def __init__(self):
            self.events: List[StreamEvent] = []
        
        async def __call__(self, event: StreamEvent):
            self.events.append(event)
    
    return StreamCollector()


@pytest.fixture
def mock_cancel_event():
    """Create a cancel event that is not set."""
    return asyncio.Event()


# =============================================================================
# Configuration Tests
# =============================================================================

class TestChatAgentConfig:
    """Test chat agent configuration."""
    
    def test_agent_has_correct_config(self):
        """Test that chat agent is properly configured."""
        agent = ChatAgent()
        assert agent.config.name == "chat-agent"
        assert agent.config.display_name == "Chat Agent"
        assert "web_search" in agent.config.tools
        assert "get_weather" in agent.config.tools
        assert "document_search" in agent.config.tools
    
    def test_agent_is_streaming_agent(self):
        """Test that chat agent extends BaseStreamingAgent."""
        assert isinstance

*[truncated — see source for full prompt]*