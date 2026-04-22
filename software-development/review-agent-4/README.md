# Review Agent

> """Review Agent for automated code quality analysis (Sprint 10).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Review Agent for automated code quality analysis (Sprint 10).

The Review Agent analyzes code changes for quality, security, and performance issues.
It performs automated code review by scanning files for common patterns that indicate
potential problems, then stores findings in the database and creates blockers for
critical/high severity issues.

Key Features:
    - Security vulnerability detection (SQL injection, hardcoded secrets, command injection)
    - Performance issue detection (nested loops, O(n²) complexity)
    - Code quality analysis (high cyclomatic complexity, deep nesting)
    - Automatic blocker creation for critical findings
    - WebSocket broadcast support for real-time UI updates

Architecture:
    The ReviewAgent uses pattern-matching heuristics to analyze code files. In production,
    it would integrate with Claude Code's reviewing-code skill for deeper analysis.

Usage:
    >>> from codeframe.agents.review_agent import ReviewAgent
    >>> from codeframe.persistence.database import Database
    >>>
    >>> db = Database(":memory:")
    >>> agent = ReviewAgent(agent_id="review-001", db=db, project_id=1)
    >>> result = await agent.execute_task(task)
    >>> print(f"Found {len(result.findings)} issues, status: {result.status}")

See Also:
    - codeframe.core.models.CodeReview: Data model for review findings
    - codeframe.persistence.database.Database: Database methods for storing reviews
    - specs/015-review-polish/: Full specification for Review & Polish sprint
"""

import logging
from typing import List, Optional, Dict, Any
from dataclasses import dataclass

from codeframe.core.models import (
    Task,
    CodeReview,
    Severity,
    ReviewCategory,
    BlockerType,
)
from codeframe.persistence.database import Database

logger = logging.getLogger(__name__)


@dataclass
class ReviewResult:
    """Result of code review execution.

    Attributes:
        status: Review status - "completed" (no critical issues), "blocked" (critical iss

*[truncated — see source for full prompt]*