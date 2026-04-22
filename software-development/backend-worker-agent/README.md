# Backend Worker Agent

> """
Backend Worker Agent - Autonomous task execution (cf-41).

This agent reads tasks from the database, builds context from the codebase index,
gener

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Backend Worker Agent - Autonomous task execution (cf-41).

This agent reads tasks from the database, builds context from the codebase index,
generates Python code using LLM, writes files, and updates task status.

Key responsibilities:
- Fetch pending tasks from database
- Build execution context from codebase index
- Generate code via Anthropic Claude API
- Apply file changes safely
- Update task status
- Error handling and retry logic

Phase 1 Implementation: Foundation (initialization and task fetching)
"""

import logging
import os
from typing import Dict, Any, Optional, List
import json
import asyncio
from datetime import datetime
from pathlib import Path

from codeframe.persistence.database import Database
from codeframe.indexing.codebase_index import CodebaseIndex
from codeframe.core.models import TaskStatus
from codeframe.providers.sdk_client import SDKClientWrapper
from codeframe.adapters.llm import LLMProvider, Purpose, get_provider


logger = logging.getLogger(__name__)


class BackendWorkerAgent:
    """
    Autonomous agent that executes backend development tasks.

    The agent operates in a loop:
    1. Fetch highest priority pending task
    2. Build context from codebase
    3. Generate code using LLM
    4. Write files to disk
    5. Update task status
    6. Repeat

    Integration points:
    - Database (cf-8): Task queue and status management
    - CodebaseIndex (cf-32): Symbol and file discovery
    - Anthropic Claude API: Code generation
    - Git Workflow (cf-33): Feature branch context
    - Test Runner (cf-42): Future integration
    - Self-Correction (cf-43): Future integration
    """

    def __init__(
        self,
        db: Database,
        codebase_index: CodebaseIndex,
        provider: str = "claude",
        api_key: Optional[str] = None,
        project_root: str = ".",
        ws_manager=None,
        use_sdk: bool = True,
        llm_provider: Optional[LLMProvider] = None,
    ):
        """
        Initialize Backend Wor

*[truncated — see source for full prompt]*