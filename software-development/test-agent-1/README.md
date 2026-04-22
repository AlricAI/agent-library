# Test Agent

> """
Test Agent.

A minimal agent for validation tests. Uses the "test" purpose from
provision/ansible/group_vars/all/model_registry.yml — currently th

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Test Agent.

A minimal agent for validation tests. Uses the "test" purpose from
provision/ansible/group_vars/all/model_registry.yml — currently the smallest
available Qwen model (Qwen3.5-0.8B family) — and has no tools enabled.
Designed for quick, deterministic testing of the LLM chain.

Used by the deploy service's validate_llm_chain endpoint to verify the full pipeline:
Direct LLM -> LiteLLM -> Agent API
"""

import logging
import os
from typing import List

from pydantic_ai import Agent
from pydantic_ai.models.openai import OpenAIChatModel

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    ToolStrategy,
)

logger = logging.getLogger(__name__)


# Test agent system prompt - focused on direct, deterministic responses
# /no_think disables Qwen3's reasoning mode for cleaner, faster responses
TEST_SYSTEM_PROMPT = """/no_think
You are a test assistant used for validating the LLM pipeline.

**Important Instructions:**
1. Answer questions directly and concisely
2. For math questions, respond with ONLY the number (e.g., "4" not "The answer is 4")
3. Do not use tools - answer from your knowledge only
4. Keep responses short (under 100 tokens)

This agent is used for automated testing. Responses should be predictable and verifiable."""


class TestAgent(BaseStreamingAgent):
    """
    A minimal test agent that:
    1. Uses the smallest/fastest model available ("test" purpose from the
       model registry — currently Qwen3.5-0.8B)
    2. Has no tools enabled
    3. Provides direct, deterministic responses
    
    Used for LLM chain validation testing.
    
    Uses LLM_DRIVEN strategy which directly calls the LLM (synthesis_agent) without
    needing any tools. This ensures we get a direct LLM response.
    """
    
    def __init__(self):
        # Use an overridable model alias so validation works with restricted LiteLLM keys.
        # Priority: explicit TEST_AGENT_MODEL -> "fast"

*[truncated — see source for full prompt]*