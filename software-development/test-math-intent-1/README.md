# Test Math Intent

> """Tests for math intent classification, code generation, and retrieval filtering in LearningAgent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for math intent classification, code generation, and retrieval filtering in LearningAgent.

Covers:
- _compute_math_result(): number extraction and arithmetic evaluation
- _concept_retrieval(): keyword extraction and bigram phrase generation
- _category_instructions: category-specific synthesis prompt dispatch
- _detect_intent(): intent classification with math_type field
- Q&A echo filtering: removal of self-learning echoes from retrieval results
- SUMMARY conditional filter: meta_memory-only filtering of summary facts

Philosophy:
- Mock all LLM calls so tests run without API keys
- Test logic and control flow, not the LLM itself
- Verify edge cases: missing numbers, invalid expressions, empty inputs
"""

from __future__ import annotations

import json
from pathlib import Path
from unittest.mock import AsyncMock, MagicMock, patch

import pytest

from amplihack.agents.goal_seeking import LearningAgent


def _make_llm_response(content: str) -> str:
    """Build a mock LLM completion return value (now returns string directly)."""
    return content


class TestComputeMathResult:
    """Tests for LearningAgent._compute_math_result()."""

    @pytest.fixture(autouse=True)
    def setup_agent(self, tmp_path: Path):
        self.agent = LearningAgent(agent_name="test_math", storage_path=str(tmp_path))
        yield
        self.agent.close()

    @pytest.mark.asyncio
    @patch("amplihack.agents.goal_seeking.learning_agent.completion", new_callable=AsyncMock)
    async def test_percentage_computation(self, mock_completion: AsyncMock):
        """Percentage: (2.3 - 2.0) / 2.0 * 100 = 15."""
        mock_completion.return_value = _make_llm_response(
            json.dumps(
                {
                    "numbers": {"old": 2.0, "new": 2.3},
                    "expression": "(2.3 - 2.0) / 2.0 * 100",
                    "description": "percentage increase",
                }
            )
        )

        facts = [{"outcome": "Budget was 2.0M, now 2.3M"}]


*[truncated — see source for full prompt]*