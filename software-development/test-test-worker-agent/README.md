# Test Test Worker Agent

> """
Tests for Test Worker Agent (Sprint 4: cf-49).
"""

import pytest
from unittest.mock import Mock, patch
from codeframe.adapters.llm import MockPro

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Tests for Test Worker Agent (Sprint 4: cf-49).
"""

import pytest
from unittest.mock import Mock, patch
from codeframe.adapters.llm import MockProvider

from codeframe.agents.test_worker_agent import TestWorkerAgent


@pytest.fixture
def temp_tests_dir(tmp_path):
    """Create temporary tests directory."""
    tests_dir = tmp_path / "tests"
    tests_dir.mkdir()
    return tests_dir


@pytest.fixture
def test_agent(temp_tests_dir):
    """Create TestWorkerAgent for testing."""
    agent = TestWorkerAgent(agent_id="test-agent-001", provider="anthropic", api_key="test-key")
    agent.tests_dir = temp_tests_dir
    agent.project_root = temp_tests_dir.parent
    return agent


@pytest.fixture
def sample_task():
    """Create sample task dict for testing (matches LeadAgent's task.to_dict() output)."""
    return {
        "id": 1,
        "project_id": 1,
        "issue_id": 1,
        "task_number": "T-001",
        "parent_issue_number": "I-001",
        "title": "Create tests for UserService",
        "description": "Generate tests for codeframe/services/user_service.py",
        "status": "pending",
        "assigned_to": None,
        "depends_on": "",
        "can_parallelize": False,
        "priority": 1,
        "workflow_step": 1,
        "requires_mcp": False,
        "estimated_tokens": 0,
        "actual_tokens": None,
    }


class TestTestWorkerAgentInitialization:
    """Test agent initialization."""

    @pytest.mark.asyncio
    async def test_initialization_with_defaults(self):
        """Test agent initializes with default values."""
        agent = TestWorkerAgent(agent_id="test-001")

        assert agent.agent_id == "test-001"
        assert agent.agent_type == "test"
        assert agent.provider == "anthropic"
        assert agent.max_correction_attempts == 3

    @pytest.mark.asyncio
    async def test_initialization_with_custom_attempts(self):
        """Test agent initializes with custom correction attempts."""
        agent = TestWorkerAge

*[truncated — see source for full prompt]*