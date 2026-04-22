# Test Agent

> """Test core agent functionality.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Test core agent functionality."""

from unittest.mock import AsyncMock, patch

import pytest
from pydantic_ai.messages import ModelTextResponse
from pydantic_ai.models.function import FunctionModel
from pydantic_ai.models.test import TestModel

from ..agent import SearchResponse, interactive_search, search, search_agent
from ..dependencies import AgentDependencies


class TestAgentInitialization:
    """Test agent initialization and configuration."""

    def test_agent_has_correct_model_type(self, test_agent):
        """Test agent is configured with correct model type."""
        assert test_agent.model is not None
        assert isinstance(test_agent.model, TestModel)

    def test_agent_has_dependencies_type(self, test_agent):
        """Test agent has correct dependencies type."""
        assert test_agent.deps_type == AgentDependencies

    def test_agent_has_system_prompt(self, test_agent):
        """Test agent has system prompt configured."""
        assert test_agent.system_prompt is not None
        assert len(test_agent.system_prompt) > 0
        assert "semantic search" in test_agent.system_prompt.lower()

    def test_agent_has_registered_tools(self, test_agent):
        """Test agent has all required tools registered."""
        tool_names = [tool.name for tool in test_agent.tool_defs]
        expected_tools = ['semantic_search', 'hybrid_search', 'auto_search', 'set_search_preference']

        for expected_tool in expected_tools:
            assert expected_tool in tool_names, f"Missing tool: {expected_tool}"


class TestAgentBasicFunctionality:
    """Test basic agent functionality with TestModel."""

    @pytest.mark.asyncio
    async def test_agent_responds_to_simple_query(self, test_agent, test_dependencies):
        """Test agent provides response to simple query."""
        deps, connection = test_dependencies

        result = await test_agent.run(
            "Search for Python tutorials",
            deps=deps
        )

        assert re

*[truncated — see source for full prompt]*