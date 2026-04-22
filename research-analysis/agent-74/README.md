# Agent

> """
Seek - Deep Research Agent
===========================

Self-learning deep research agent. Given a topic, person, or company, Seek does
exhaustive

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Seek - Deep Research Agent
===========================

Self-learning deep research agent. Given a topic, person, or company, Seek does
exhaustive multi-source research and produces structured reports. Learns what
sources are reliable, what research patterns work, and what the user cares about.

Test:
    python -m agents.seek.agent
"""

from os import getenv

from agno.agent import Agent
from agno.learn import (
    LearnedKnowledgeConfig,
    LearningMachine,
    LearningMode,
)
from agno.models.openai import OpenAIResponses
from agno.tools.mcp import MCPTools
from agno.tools.parallel import ParallelTools
from db import create_knowledge, get_postgres_db

# ---------------------------------------------------------------------------
# Setup
# ---------------------------------------------------------------------------
agent_db = get_postgres_db()

# Dual knowledge system
seek_knowledge = create_knowledge("Seek Knowledge", "seek_knowledge")
seek_learnings = create_knowledge("Seek Learnings", "seek_learnings")

# ---------------------------------------------------------------------------
# Tools
# ---------------------------------------------------------------------------
EXA_API_KEY = getenv("EXA_API_KEY", "")
EXA_MCP_URL = (
    f"https://mcp.exa.ai/mcp?exaApiKey={EXA_API_KEY}&tools="
    "web_search_exa,"
    "company_research_exa,"
    "crawling_exa,"
    "people_search_exa,"
    "get_code_context_exa"
)

seek_tools: list = [
    MCPTools(url=EXA_MCP_URL),
    ParallelTools(enable_extract=False),
]

# ---------------------------------------------------------------------------
# Instructions
# ---------------------------------------------------------------------------
instructions = """\
You are Seek, a self-learning deep research agent.

## Your Purpose

Given any topic, person, company, or question, you conduct exhaustive multi-source research and produce structured, well-sourced reports.
You learn what sources are reliable, what research patterns work, and wh

*[truncated — see source for full prompt]*