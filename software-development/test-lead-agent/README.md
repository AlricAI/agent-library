# Test Lead Agent

> """Tests for Lead Agent with Anthropic integration.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for Lead Agent with Anthropic integration.

Following TDD: These tests are written FIRST, before implementation.
Target: >90% coverage for lead_agent.py module.
"""

import pytest
from unittest.mock import Mock, patch
from codeframe.agents.lead_agent import LeadAgent
from codeframe.persistence.database import Database
from codeframe.core.models import TaskStatus


@pytest.mark.unit
class TestLeadAgentInitialization:
    """Test Lead Agent initialization."""

    def test_lead_agent_initialization_with_database(self, temp_db_path):
        """Test that Lead Agent initializes with database connection."""
        # ARRANGE
        db = Database(temp_db_path)
        db.initialize()
        project_id = db.create_project("test-project", "Test Project project")

        # ACT
        agent = LeadAgent(project_id=project_id, db=db, api_key="sk-ant-test-key")

        # ASSERT
        assert agent.project_id == project_id
        assert agent.db is not None
        assert agent.provider is not None

    def test_lead_agent_initialization_without_api_key_raises_error(self, temp_db_path):
        """Test that Lead Agent fails fast when API key is missing."""
        # ARRANGE
        db = Database(temp_db_path)
        db.initialize()
        project_id = db.create_project("test-project", "Test Project project")

        # ACT & ASSERT
        with pytest.raises(ValueError) as exc_info:
            LeadAgent(project_id=project_id, db=db, api_key=None)

        assert "api_key" in str(exc_info.value).lower() or "ANTHROPIC" in str(exc_info.value)

    def test_lead_agent_loads_existing_conversation(self, temp_db_path):
        """Test that Lead Agent loads existing conversation from database."""
        # ARRANGE
        db = Database(temp_db_path)
        db.initialize()
        project_id = db.create_project("test-project", "Test Project project")

        # Add some conversation history
        db.create_memory(project_id, "conversation", "user", "Hello")
        d

*[truncated — see source for full prompt]*