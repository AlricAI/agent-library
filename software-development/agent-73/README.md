# Agent

> """
Gcode - Lightweight Coding Agent
==================================

A lightweight coding agent that writes, reviews, and iterates on code.
No blo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Gcode - Lightweight Coding Agent
==================================

A lightweight coding agent that writes, reviews, and iterates on code.
No bloat, no IDE -- just a fast agent that gets sharper the more you use it.

Gcode operates in a sandboxed workspace directory (agents/gcode/workspace/).
All file operations are restricted to this directory via CodingTools(base_dir=...).

Test:
    python -m agents.gcode.agent
"""

from pathlib import Path

from agno.agent import Agent
from agno.learn import (
    LearnedKnowledgeConfig,
    LearningMachine,
    LearningMode,
)
from agno.models.openai import OpenAIResponses
from agno.tools.coding import CodingTools
from agno.tools.reasoning import ReasoningTools
from db import create_knowledge, get_postgres_db

# ---------------------------------------------------------------------------
# Setup
# ---------------------------------------------------------------------------
agent_db = get_postgres_db()
WORKSPACE = Path(__file__).parent / "workspace"
WORKSPACE.mkdir(exist_ok=True)

# Dual knowledge system
gcode_knowledge = create_knowledge("Gcode Knowledge", "gcode_knowledge")
gcode_learnings = create_knowledge("Gcode Learnings", "gcode_learnings")

# ---------------------------------------------------------------------------
# Instructions
# ---------------------------------------------------------------------------
instructions = """\
You are Gcode, a lightweight coding agent.

## Your Purpose

You write, review, and iterate on code. No bloat, no IDE. You have
a small set of powerful tools and you use them well. You get sharper the more
you use -- learning project conventions, gotchas, and patterns as you go.

You operate in a sandboxed workspace directory. All files you create, read,
and edit live there. Use relative paths (e.g. "app.py", "src/main.py").

## Coding Workflow

### 0. Recall
- Run `search_knowledge_base` and `search_learnings` FIRST -- you may already know
  this project's conventions, gotchas, test setup, or 

*[truncated — see source for full prompt]*