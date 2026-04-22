# Translator

> """
Logic Translator Agent for Java to JavaScript code conversion
Enhanced for Issue #546: Block Generation from Java block analysis
"""

from typing 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Logic Translator Agent for Java to JavaScript code conversion
Enhanced for Issue #546: Block Generation from Java block analysis
"""

from typing import List, Dict, Any, Optional

import json

try:
    import tree_sitter_java as ts_java
    from tree_sitter import Language, Parser

    TREE_SITTER_AVAILABLE = True
except ImportError:
    TREE_SITTER_AVAILABLE = False
    ts_java = None
    Parser = None
from models.smart_assumptions import (
    SmartAssumptionEngine,
)
from agents.java_analyzer import JavaAnalyzerAgent
from utils.logging_config import get_agent_logger, log_performance

from agents.logic_translator.block_templates import (
    BEDROCK_BLOCK_TEMPLATES,
    BEDROCK_ITEM_TEMPLATES,
    BEDROCK_ENTITY_TEMPLATES,
    BEDROCK_RECIPE_TEMPLATES,
    JAVA_TO_BEDROCK_ITEM_PROPERTIES,
    JAVA_ITEM_METHOD_MAPPINGS,
    JAVA_TO_BEDROCK_ENTITY_PROPERTIES,
)
from agents.logic_translator.block_state_mapper import (
    JAVA_TO_BEDROCK_BLOCK_PROPERTIES,
    JAVA_BLOCK_METHOD_MAPPINGS,
    BlockStateMapper,
)
from agents.logic_translator.assumptions import SMART_ASSUMPTIONS, get_smart_assumptions

# Use enhanced agent logger
logger = get_agent_logger("logic_translator")

# LLM Translation temperature for code generation (per research: 0.2 is optimal)
LLM_CODE_TEMPERATURE = 0.2


# Templates loaded from block_templates module# Smart assumptions loaded from assumptions module


# Block property mappings loaded from block_state_mapper module
class LogicTranslatorAgent:
    """
    Logic Translator Agent responsible for converting Java logic to Bedrock-compatible
    JavaScript as specified in PRD Feature 2.
    """

    _instance = None

    def __init__(self):
        self.logger = logger
        self.smart_assumption_engine = SmartAssumptionEngine()
        self.java_analyzer_agent = JavaAnalyzerAgent()

        self._conversion_rag_pipeline = None
        self._rag_context_enabled = False

        # Java to JavaScript conversion mappings
        self.type_mappin

*[truncated — see source for full prompt]*