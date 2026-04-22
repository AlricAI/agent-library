# Logic Auditor Agent

> """
Adversarial Logic Auditor Agent for QA pipeline.

Detects subtle functional discrepancies — conversions that pass syntax and schema
checks but sil

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Adversarial Logic Auditor Agent for QA pipeline.

Detects subtle functional discrepancies — conversions that pass syntax and schema
checks but silently break gameplay behavior. Based on ASMR-Bench framework.

This is the adversarial logic auditor (QA-06) in the multi-agent QA pipeline.
"""

import re
import time
from dataclasses import dataclass, field
from enum import Enum
from pathlib import Path
from typing import Any, Dict, List, Optional, Tuple

import structlog

from qa.context import QAContext
from qa.validators import AgentOutput, validate_agent_output

logger = structlog.get_logger(__name__)

TEMPERATURE_ZERO = 0.0


class Severity(Enum):
    HIGH = "high"
    MEDIUM = "medium"
    LOW = "low"


class SemanticType(Enum):
    NUMERIC_FORMULA = "numeric_formula"
    PROBABILITY_RNG = "probability_rng"
    EVENT_HOOK = "event_hook"
    CONDITIONAL = "conditional"
    RESOURCE_ID = "resource_id"
    UNKNOWN = "unknown"


@dataclass
class AuditFinding:
    check_type: str
    severity: Severity
    description: str
    java_snippet: str
    bedrock_snippet: str
    expected_behavior: str = ""
    actual_behavior: str = ""

    def to_dict(self) -> Dict[str, Any]:
        return {
            "check_type": self.check_type,
            "severity": self.severity.value,
            "description": self.description,
            "java_snippet": self.java_snippet,
            "bedrock_snippet": self.bedrock_snippet,
            "expected_behavior": self.expected_behavior,
            "actual_behavior": self.actual_behavior,
        }


@dataclass
class AuditReport:
    findings: List[AuditFinding] = field(default_factory=list)
    high_severity_count: int = 0
    medium_severity_count: int = 0
    low_severity_count: int = 0
    blocked: bool = False
    confidence_impact: float = 0.0

    def to_dict(self) -> Dict[str, Any]:
        return {
            "findings": [f.to_dict() for f in self.findings],
            "high_severity_count": self.high_severity_count,
  

*[truncated — see source for full prompt]*