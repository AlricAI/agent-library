# Test Temporal Reasoning

> """Tests for LearningAgent with mocked LLM.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for LearningAgent with mocked LLM.

Philosophy:
- Test without requiring API keys
- Mock LLM for predictable results
- Verify learning and question-answering flow
"""

import shutil
import tempfile
from pathlib import Path
from unittest.mock import AsyncMock, patch

import pytest

from amplihack.agents.goal_seeking import LearningAgent


class TestTemporalCodeGeneration:
    """Test suite for temporal reasoning code generation."""

    @pytest.fixture
    def temp_storage(self):
        """Create temporary storage directory."""
        temp_dir = Path(tempfile.mkdtemp())
        yield temp_dir
        if temp_dir.exists():
            shutil.rmtree(temp_dir)

    @pytest.fixture
    def agent(self, temp_storage):
        """Create LearningAgent with temporary storage."""
        agent = LearningAgent(agent_name="test_temporal", storage_path=str(temp_storage))
        yield agent
        agent.close()

    # -- _parse_temporal_index tests --

    def test_parse_first_keyword(self, agent):
        """Test 'first' maps to index 0."""
        result = agent._parse_temporal_index("What was the first value?")
        assert result == "0"

    def test_parse_original_keyword(self, agent):
        """Test 'original' maps to index 0."""
        result = agent._parse_temporal_index("What was the original deadline?")
        assert result == "0"

    def test_parse_second_keyword(self, agent):
        """Test 'second' maps to index 1."""
        result = agent._parse_temporal_index("What was the second value in the chain?")
        assert result == "1"

    def test_parse_intermediate_keyword(self, agent):
        """Test 'intermediate' maps to middle index."""
        result = agent._parse_temporal_index("What was the intermediate value?")
        assert result == "len(transitions) // 2"

    def test_parse_latest_keyword(self, agent):
        """Test 'latest' maps to index -1."""
        result = agent._parse_temporal_index("What is the latest deadline?")
        as

*[truncated — see source for full prompt]*