# Review Worker Agent

> """ReviewWorkerAgent for automated code quality reviews.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""ReviewWorkerAgent for automated code quality reviews.

Performs automated code reviews using complexity analysis, security scanning,
and OWASP pattern detection.
"""

import logging
from pathlib import Path
from typing import List

from codeframe.agents.worker_agent import WorkerAgent
from codeframe.core.models import ReviewReport, ReviewFinding
from codeframe.lib.quality.complexity_analyzer import ComplexityAnalyzer
from codeframe.lib.quality.security_scanner import SecurityScanner
from codeframe.lib.quality.owasp_patterns import OWASPPatterns
from codeframe.persistence.database import Database

logger = logging.getLogger(__name__)


class ReviewWorkerAgent(WorkerAgent):
    """Worker agent that performs automated code reviews.

    Review scoring algorithm:
    - Complexity: 30% weight
    - Security: 40% weight (highest priority)
    - Style: 20% weight
    - Coverage: 10% weight

    Decision thresholds:
    - 90-100: Excellent (approve)
    - 70-89: Good (approve with suggestions)
    - 50-69: Needs improvement (request changes, create blocker)
    - 0-49: Poor (reject, create blocker)

    Max review iterations: 2
    """

    # Score thresholds
    EXCELLENT_THRESHOLD = 90
    GOOD_THRESHOLD = 70
    ACCEPTABLE_THRESHOLD = 50

    # Scoring weights
    COMPLEXITY_WEIGHT = 0.3
    SECURITY_WEIGHT = 0.4
    STYLE_WEIGHT = 0.2
    COVERAGE_WEIGHT = 0.1

    # Max re-review iterations
    MAX_ITERATIONS = 2

    def __init__(self, agent_id: str, db: Database, provider: str = "anthropic"):
        """Initialize ReviewWorkerAgent.

        Args:
            agent_id: Unique agent identifier
            db: Database instance
            provider: LLM provider (default: anthropic)
        """
        super().__init__(
            agent_id=agent_id,
            agent_type="review",
            provider=provider,
            db=db,
        )

        # Initialize quality analyzers
        # We'll set the project_path dynamically when executing tasks
        self.com

*[truncated — see source for full prompt]*