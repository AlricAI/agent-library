# Gameplay Comparison Agent

> """
Direct Gameplay Comparison Agent

This agent implements Mode 1 of the AI-Powered Validation & Comparison system.
It launches Minecraft (Java and B

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Direct Gameplay Comparison Agent

This agent implements Mode 1 of the AI-Powered Validation & Comparison system.
It launches Minecraft (Java and Bedrock) locally, runs automated test scripts,
captures screenshots, and compares visual/functional differences between the
original Java mod and converted Bedrock addon.

Issue: #494 (Phase 4a)
"""

import os
import time
import json
import subprocess
import hashlib
from datetime import datetime
from typing import Any, Dict, List, Optional
from dataclasses import dataclass
from pathlib import Path


@dataclass
class GameTestScript:
    """Represents a test script to run in Minecraft."""

    name: str
    commands: List[str]
    expected_results: List[str]
    timeout_seconds: int = 60


@dataclass
class Screenshot:
    """Represents a captured screenshot."""

    path: str
    timestamp: datetime
    game_version: str
    test_name: str
    hash: str
    edition: Optional[str] = None  # Explicit game edition (e.g. "java", "bedrock")


@dataclass
class GameplayComparisonResult:
    """Results from comparing gameplay between Java and Bedrock."""

    conversion_id: str
    java_screenshots: List[Screenshot]
    bedrock_screenshots: List[Screenshot]
    visual_diffs: List[Dict[str, Any]]
    functional_tests: List[Dict[str, Any]]
    overall_score: float
    missing_features: List[str]
    recommendations: List[str]


class MinecraftLauncher:
    """Handles launching Minecraft instances."""

    def __init__(self, java_path: Optional[str] = None, bedrock_path: Optional[str] = None):
        self.java_path = java_path or os.environ.get(
            "MINECRAFT_JAVA_PATH", "/opt/minecraft-launcher"
        )
        self.bedrock_path = bedrock_path or os.environ.get(
            "MINECRAFT_BEDROCK_PATH", "/opt/minecraft-bedrock"
        )
        self.running_instances: Dict[str, Optional[subprocess.Popen[Any]]] = {}

    def is_java_installed(self) -> bool:
        """Check if Java Minecraft is available."""
        return 

*[truncated — see source for full prompt]*