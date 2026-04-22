# Multi Agent

> """Multi-Agent Learning Agent: Drop-in replacement for LearningAgent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Multi-Agent Learning Agent: Drop-in replacement for LearningAgent.

Philosophy:
- Same external interface as LearningAgent (learn_from_content, answer_question)
- Internally decomposes into Coordinator + MemoryAgent + synthesis
- MemoryAgent handles retrieval strategy selection
- Coordinator determines the execution plan
- Backward compatible: if something fails, falls back to parent LearningAgent
- When enable_spawning=True, can dynamically spawn sub-agents for multi-hop reasoning

Public API:
    MultiAgentLearningAgent: Drop-in replacement with multi-agent retrieval
"""

from __future__ import annotations

import logging
from pathlib import Path
from typing import Any

from ..learning_agent import LearningAgent
from ..similarity import rerank_facts_by_query
from .agent_spawner import AgentSpawner
from .coordinator import CoordinatorAgent
from .memory_agent import MemoryAgent

logger = logging.getLogger(__name__)


class MultiAgentLearningAgent(LearningAgent):
    """Learning agent with multi-agent internal architecture.

    Extends LearningAgent by replacing the monolithic retrieval+synthesis
    pipeline with:
    - CoordinatorAgent: classifies questions and routes to specialists
    - MemoryAgent: selects optimal retrieval strategy per question
    - AgentSpawner (optional): spawns sub-agents for multi-hop reasoning

    The synthesis step still uses the parent LearningAgent's _synthesize_with_llm
    because the LLM prompt engineering for different question types is extensive
    and well-tested. The key improvement is in RETRIEVAL, not synthesis.

    Args:
        agent_name: Name for the agent
        model: LLM model to use
        storage_path: Custom storage path for memory
        use_hierarchical: Must be True for multi-agent benefits
        enable_spawning: If True, enable dynamic sub-agent spawning

    Example:
        >>> agent = MultiAgentLearningAgent(
        ...     "multi_agent_eval",
        ...     use_hierarchical=True,
        ...    

*[truncated — see source for full prompt]*