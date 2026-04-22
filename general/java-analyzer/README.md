# Java Analyzer

> """
Java Analyzer Agent for analyzing Java mod structure and extracting features.

This module provides the main JavaAnalyzerAgent class which combine

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Java Analyzer Agent for analyzing Java mod structure and extracting features.

This module provides the main JavaAnalyzerAgent class which combines functionality from:
- archive_reader: JAR/ZIP extraction
- framework_detector: Forge/Fabric/Quilt detection
- feature_extractor: AST-based feature extraction
- embedding_bridge: embedding generation
- llm_analyzer: LLM complexity analysis
- tools: CrewAI @tool wrappers
"""

import json
import os
import re
import time
import zipfile
from pathlib import Path
from typing import List, Dict, Union, Optional, Any

from crewai.tools import tool
from models.smart_assumptions import SmartAssumptionEngine
from utils.embedding_generator import LocalEmbeddingGenerator
from utils.logging_config import get_agent_logger, log_performance
from agents.java_semantic_chunker import JavaSemanticChunker, ChunkManifest

from agents.java_analyzer.archive_reader import (
    ArchiveReader,
    FEATURE_ANALYSIS_FILE_LIMIT,
    METADATA_AST_FILE_LIMIT,
    DEPENDENCY_ANALYSIS_FILE_LIMIT,
)
from agents.java_analyzer.framework_detector import FrameworkDetector
from agents.java_analyzer.feature_extractor import FeatureExtractor, _class_name_to_registry_name
from agents.java_analyzer.embedding_bridge import EmbeddingBridge
from agents.java_analyzer.llm_analyzer import LLMAnalyzer
from agents.java_analyzer.tools import JavaAnalyzerTools

logger = get_agent_logger("java_analyzer")


class JavaAnalyzerAgent:
    """
    Java Analyzer Agent responsible for analyzing Java mod structure,
    dependencies, and features as specified in PRD Feature 2.
    """

    _instance = None

    analyze_mod_structure_tool = JavaAnalyzerTools.analyze_mod_structure_tool
    extract_mod_metadata_tool = JavaAnalyzerTools.extract_mod_metadata_tool
    identify_features_tool = JavaAnalyzerTools.identify_features_tool
    analyze_dependencies_tool = JavaAnalyzerTools.analyze_dependencies_tool
    extract_assets_tool = JavaAnalyzerTools.extract_assets_tool
    analyze_compl

*[truncated — see source for full prompt]*