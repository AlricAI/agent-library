# Test Backend Worker Agent

> """
Tests for Backend Worker Agent (cf-41).

Test coverage for autonomous task execution:
- Initialization and configuration
- Task fetching from data

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Tests for Backend Worker Agent (cf-41).

Test coverage for autonomous task execution:
- Initialization and configuration
- Task fetching from database
- Context building from codebase index
- Code generation via LLM
- File operations (create/modify/delete)
- Task execution orchestration

Following strict TDD methodology (RED-GREEN-REFACTOR).
"""

import pytest
from unittest.mock import Mock, patch
import json

from codeframe.agents.backend_worker_agent import BackendWorkerAgent
from codeframe.adapters.llm import LLMResponse
from codeframe.persistence.database import Database
from codeframe.indexing.codebase_index import CodebaseIndex
from codeframe.core.models import TaskStatus, Task


class TestBackendWorkerAgentInitialization:
    """Test agent initialization and configuration."""

    def test_init_with_required_parameters(self, tmp_path):
        """Test agent initializes with required parameters."""
        db = Mock(spec=Database)
        index = Mock(spec=CodebaseIndex)

        agent = BackendWorkerAgent(db=db, codebase_index=index, project_root=tmp_path)

        assert agent.db == db
        assert agent.codebase_index == index
        assert agent.project_root == tmp_path

    def test_init_with_default_provider(self, tmp_path):
        """Test agent defaults to 'claude' provider."""
        db = Mock(spec=Database)
        index = Mock(spec=CodebaseIndex)

        agent = BackendWorkerAgent(db=db, codebase_index=index, project_root=tmp_path)

        assert agent.provider == "claude"

    def test_init_with_custom_provider(self, tmp_path):
        """Test agent accepts custom provider."""
        db = Mock(spec=Database)
        index = Mock(spec=CodebaseIndex)

        agent = BackendWorkerAgent(
            db=db, codebase_index=index, provider="gpt4", project_root=tmp_path
        )

        assert agent.provider == "gpt4"

    def test_init_with_api_key(self, tmp_path):
        """Test agent accepts API key for LLM provider."""
        db = Mock(

*[truncated — see source for full prompt]*