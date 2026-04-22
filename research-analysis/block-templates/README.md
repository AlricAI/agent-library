# Block Templates

> """
Bedrock template data for block, item, entity, and recipe generation.

Loads templates from ai-engine/data/bedrock_block_templates.json.
"""

impo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Bedrock template data for block, item, entity, and recipe generation.

Loads templates from ai-engine/data/bedrock_block_templates.json.
"""

import json
import os
from pathlib import Path
from typing import Dict, Any

try:
    import tree_sitter_java as ts_java
    from tree_sitter import Language, Parser

    TREE_SITTER_AVAILABLE = True
except ImportError:
    TREE_SITTER_AVAILABLE = False
    ts_java = None
    Parser = None


def _get_data_path() -> Path:
    current_dir = Path(__file__).parent
    return current_dir.parent.parent / "data" / "bedrock_block_templates.json"


def load_templates() -> Dict[str, Any]:
    """Load all templates from the JSON data file."""
    data_path = _get_data_path()
    with open(data_path, "r") as f:
        return json.load(f)


TEMPLATE_DATA = load_templates()

BEDROCK_BLOCK_TEMPLATES = TEMPLATE_DATA["block_templates"]
BEDROCK_ITEM_TEMPLATES = TEMPLATE_DATA["item_templates"]
BEDROCK_ENTITY_TEMPLATES = TEMPLATE_DATA["entity_templates"]
BEDROCK_RECIPE_TEMPLATES = TEMPLATE_DATA["recipe_templates"]
JAVA_TO_BEDROCK_ITEM_PROPERTIES = TEMPLATE_DATA["java_to_bedrock_item_properties"]
JAVA_ITEM_METHOD_MAPPINGS = TEMPLATE_DATA["java_item_method_mappings"]
JAVA_TO_BEDROCK_ENTITY_PROPERTIES = TEMPLATE_DATA["java_to_bedrock_entity_properties"]


class BedrockTemplateLoader:
    """Loads and provides access to Bedrock template data."""

    def __init__(self):
        self._templates = TEMPLATE_DATA
        self._ts_parser = None

    @property
    def block_templates(self) -> Dict[str, Any]:
        return self._templates["block_templates"]

    @property
    def item_templates(self) -> Dict[str, Any]:
        return self._templates["item_templates"]

    @property
    def entity_templates(self) -> Dict[str, Any]:
        return self._templates["entity_templates"]

    @property
    def recipe_templates(self) -> Dict[str, Any]:
        return self._templates["recipe_templates"]

    @property
    def java_to_bedrock_item_properties(se

*[truncated — see source for full prompt]*