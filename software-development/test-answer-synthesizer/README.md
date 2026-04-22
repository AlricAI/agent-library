# Test Answer Synthesizer

> """Tests for AnswerSynthesizerMixin methods.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for AnswerSynthesizerMixin methods.

Tests _evaluate_answer_completeness (including the critical bug fix)
and answer_question_agentic entry points.
"""

import shutil
import tempfile
from pathlib import Path
from unittest.mock import AsyncMock, patch

import pytest

from amplihack.agents.goal_seeking import LearningAgent


class TestAnswerSynthesizer:
    """Tests for answer synthesis mixin methods."""

    @pytest.fixture
    def temp_storage(self):
        temp_dir = Path(tempfile.mkdtemp())
        yield temp_dir
        if temp_dir.exists():
            shutil.rmtree(temp_dir)

    @pytest.fixture
    def agent(self, temp_storage):
        agent = LearningAgent(agent_name="test_synth", storage_path=str(temp_storage))
        yield agent
        agent.close()

    # --- _evaluate_answer_completeness ---

    @pytest.mark.asyncio
    async def test_evaluate_empty_answer_is_incomplete(self, agent):
        result = await agent._evaluate_answer_completeness("What is X?", "")
        assert result["is_complete"] is False

    @pytest.mark.asyncio
    async def test_evaluate_no_info_answer_is_incomplete(self, agent):
        result = await agent._evaluate_answer_completeness(
            "What is X?", "I don't have enough information to answer."
        )
        assert result["is_complete"] is False

    @pytest.mark.asyncio
    async def test_evaluate_long_answer_is_complete(self, agent):
        long_answer = "This is a substantive answer about the topic with more than fifty characters of detail."
        result = await agent._evaluate_answer_completeness("What is X?", long_answer)
        assert result["is_complete"] is True

    @pytest.mark.asyncio
    async def test_evaluate_short_answer_calls_llm(self, agent):
        with patch(
            "amplihack.agents.goal_seeking.learning_agent._llm_completion",
            new_callable=AsyncMock,
            return_value='{"is_complete": true}',
        ):
            result = await agent._evaluate_answer_co

*[truncated — see source for full prompt]*