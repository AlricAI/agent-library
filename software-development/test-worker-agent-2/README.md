# Test Worker Agent

> """
Tests for Worker Agent token tracking functionality.

Test coverage:
- Token usage recording with valid response
- Zero token handling
- Error han

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Tests for Worker Agent token tracking functionality.

Test coverage:
- Token usage recording with valid response
- Zero token handling
- Error handling scenarios (missing project_id, database errors)
- Model name resolution
- Integration with MetricsTracker
- Execute task integration
"""

import pytest
import os
from unittest.mock import Mock, AsyncMock, patch
from codeframe.agents.worker_agent import WorkerAgent
from codeframe.core.models import Task, AgentMaturity, CallType, TaskStatus
from codeframe.persistence.database import Database
from codeframe.adapters.llm import MockProvider
from codeframe.adapters.llm.base import LLMRateLimitError, LLMConnectionError


@pytest.fixture
def db():
    """Create in-memory database for testing."""
    database = Database(":memory:")
    database.initialize()

    return database


class ErrorMockProvider(MockProvider):
    """MockProvider subclass that raises LLMConnectionError on every call."""

    async def async_complete(self, messages, purpose=None, tools=None,
                             max_tokens=4096, temperature=0.0, system=None):
        raise LLMConnectionError("Connection failed")


class RateLimitMockProvider(MockProvider):
    """MockProvider subclass that raises LLMRateLimitError on every call."""

    async def async_complete(self, messages, purpose=None, tools=None,
                             max_tokens=4096, temperature=0.0, system=None):
        raise LLMRateLimitError("Rate limit exceeded")


class FailThenSucceedMockProvider(MockProvider):
    """MockProvider that fails N times then succeeds."""

    def __init__(self, fail_count: int, default_response: str = "Task completed"):
        super().__init__(default_response=default_response)
        self.fail_count = fail_count
        self._call_count = 0

    async def async_complete(self, messages, purpose=None, tools=None,
                             max_tokens=4096, temperature=0.0, system=None):
        self._call_count += 1
        if self._cal

*[truncated — see source for full prompt]*