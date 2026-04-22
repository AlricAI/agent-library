# Agent

> """
Dash - Self-Learning Data Agent
=================================

A self-learning data agent that queries a database and provides insights.

Dash

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Dash - Self-Learning Data Agent
=================================

A self-learning data agent that queries a database and provides insights.

Dash uses a dual knowledge system:
- KNOWLEDGE: static curated knowledge (table schemas, validated queries, business rules)
- LEARNINGS: dynamic learnings it discovers through use (type gotchas, date formats, column quirks).

Test:
    python -m agents.dash.agent
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
from agno.tools.sql import SQLTools
from db import create_knowledge, db_url, get_postgres_db

from .context.business_rules import BUSINESS_CONTEXT
from .context.semantic_model import SEMANTIC_MODEL_STR
from .tools import create_introspect_schema_tool, create_save_validated_query_tool

# ---------------------------------------------------------------------------
# Setup
# ---------------------------------------------------------------------------
agent_db = get_postgres_db()

# Dual knowledge system
# - KNOWLEDGE: Static, curated (table schemas, validated queries, business rules)
# - LEARNINGS: Dynamic, discovered (type errors, date formats, business rules)
dash_knowledge = create_knowledge("Dash Knowledge", "dash_knowledge")
dash_learnings = create_knowledge("Dash Learnings", "dash_learnings")

# ---------------------------------------------------------------------------
# Tools
# ---------------------------------------------------------------------------
save_validated_query = create_save_validated_query_tool(dash_knowledge)
introspect_schema = create_introspect_schema_tool(db_url)
EXA_API_KEY = getenv("EXA_API_KEY", "")
EXA_MCP_URL = (
    f"https://mcp.exa.ai/mcp?exaApiKey={EXA_API_KEY}&tools="
    "web_search_exa,"
    "get_code_context_exa"
)

dash_tools: list = [
    SQLTools(db_url=db_url),
    introspect_schema,
    save_valid

*[truncated — see source for full prompt]*