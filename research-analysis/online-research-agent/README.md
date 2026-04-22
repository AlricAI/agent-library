# Online Research Agent

> """
Online Research Analysis Agent

This agent implements Mode 2 of the AI-Powered Validation & Comparison system.
It accepts URLs to CurseForge/Modri

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Online Research Analysis Agent

This agent implements Mode 2 of the AI-Powered Validation & Comparison system.
It accepts URLs to CurseForge/Modrinth/YouTube for original mod content,
performs multimodal analysis, generates feature checklists, and validates
the converted addon against the checklist.

Issue: #495 (Phase 4b)
"""

import os
import json
import re
import logging
from datetime import datetime
from typing import Any, Dict, List, Optional
from dataclasses import dataclass
from enum import Enum
from urllib.parse import urlparse

# Set up logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)


class SourceType(Enum):
    """Types of sources for online research."""

    CURSEFORGE = "curseforge"
    MODRINTH = "modrinth"
    YOUTUBE = "youtube"
    GENERIC_URL = "generic_url"
    UNKNOWN = "unknown"


@dataclass
class ResearchSource:
    """Represents a research source URL."""

    url: str
    source_type: SourceType
    title: str
    description: str
    metadata: Dict[str, Any]
    fetched_at: datetime


@dataclass
class FeatureChecklistItem:
    """A single feature in the checklist."""

    feature_name: str
    description: str
    category: str
    priority: str  # high, medium, low
    detected: bool
    evidence: List[str]
    validation_status: str  # verified, missing, unclear


@dataclass
class ValidationReport:
    """Report from validating converted addon against research."""

    overall_score: float
    feature_checklist: List[FeatureChecklistItem]
    verified_features: List[str]
    missing_features: List[str]
    unclear_features: List[str]
    recommendations: List[str]
    research_sources: List[ResearchSource]


class URLAnalyzer:
    """Analyzes URLs to determine source type and extract information."""

    def __init__(self):
        self.source_patterns = {
            SourceType.CURSEFORGE: [
                r"curseforge\.com/minecraft/mc-mods/([^/]+)",
                r"curseforge\.com/minecraft/mod

*[truncated — see source for full prompt]*