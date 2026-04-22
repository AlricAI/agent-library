# Status Agent

> """
Status Agent.

A project status management agent that uses predefined pipelines to execute
data operations deterministically, then lets the LLM sy

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Status Agent.

A project status management agent that uses predefined pipelines to execute
data operations deterministically, then lets the LLM synthesize results.

This avoids relying on the LLM's (often limited) ability to select and chain
multiple tools, while still leveraging LLM intelligence for:
- Classifying user intent
- Extracting structured data from freeform text
- Synthesizing human-readable responses from tool results

Architecture mirrors WebSearchAgent: deterministic pipeline + LLM synthesis.
"""

import json
import logging
import re
from typing import Any, Dict, List, Optional

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
from app.config.settings import get_settings

logger = logging.getLogger(__name__)

# Intent classification categories
INTENT_CREATE = "create"
INTENT_CONFIRM_CREATE = "confirm_create"
INTENT_QUERY = "query"
INTENT_UPDATE = "update"
INTENT_CHAT = "chat"

# Well-known data document names for the busibox-projects app
STATUS_DOC_PROJECTS = "busibox-projects-projects"
STATUS_DOC_TASKS = "busibox-projects-tasks"
STATUS_DOC_UPDATES = "busibox-projects-updates"
STATUS_SOURCE_APP = "busibox-projects"

# Synthesis prompt -- the LLM only needs to produce a nice response from tool results
STATUS_SYNTHESIS_PROMPT = """You are a project status assistant. Given tool results and user context, create a clear, well-organized response.

Guidelines:
- Start with a brief summary of what was done or found
- Use **bold** for project names and key terms
- Use bullet points for lists
- Include relevant metrics (record counts, progress %)
- Be concise and actionable
- If records were created, list what was created with a checkmark
- If querying data, format results in a readable way"""


# Extraction prompt -- used to parse user text into structured records
EXTRACT

*[truncated — see source for full prompt]*