# Agent

> """
Scout - Enterprise Knowledge Agent
===========

Test:
    python -m agents.scout.agent
"""

from os import getenv

from agno.agent import Agent
fr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Scout - Enterprise Knowledge Agent
===========

Test:
    python -m agents.scout.agent
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
from db import create_knowledge, get_postgres_db

from .context.intent_routing import INTENT_ROUTING_CONTEXT
from .context.source_registry import SOURCE_REGISTRY_STR
from .tools import (
    S3Tools,
    create_get_metadata_tool,
    create_list_sources_tool,
    create_save_intent_discovery_tool,
)

# ---------------------------------------------------------------------------
# Database & Knowledge
# ---------------------------------------------------------------------------

agent_db = get_postgres_db()

# KNOWLEDGE: Static, curated (source registry, intent routing, known patterns)
scout_knowledge = create_knowledge("Scout Knowledge", "scout_knowledge")

# LEARNINGS: Dynamic, discovered (decision traces, what worked, what didn't)
scout_learnings = create_knowledge("Scout Learnings", "scout_learnings")

# ---------------------------------------------------------------------------
# Tools
# ---------------------------------------------------------------------------

list_sources = create_list_sources_tool()
get_metadata = create_get_metadata_tool()
save_intent_discovery = create_save_intent_discovery_tool(scout_knowledge)

base_tools: list = [
    # Primary connector (S3)
    S3Tools(),
    # Awareness tools
    list_sources,
    get_metadata,
    # Learning tools
    save_intent_discovery,
    # External search
    MCPTools(
        url=f"https://mcp.exa.ai/mcp?exaApiKey={getenv('EXA_API_KEY', '')}&tools=web_search_exa"
    ),
]

# ---------------------------------------------------------------------------
# Instructions
# ---------------------------------------------------------------------------

INSTRUCTIONS = f"""\
You are Scout, a self-learn

*[truncated — see source for full prompt]*