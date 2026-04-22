# Geometry

> """
Geometry conversion module for block/item/entity models.
"""

import json
import logging
from pathlib import Path
from typing import Dict, List, O

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Geometry conversion module for block/item/entity models.
"""

import json
import logging
from pathlib import Path
from typing import Dict, List, Optional

logger = logging.getLogger(__name__)


def _convert_single_model(
    agent,
    model_path: str,
    metadata: Dict,
    entity_type: str,
    model_cache: Optional[Dict[str, Dict]] = None,
    namespace: Optional[str] = None,
) -> Dict:
    """
    Convert a Java block/item/entity model JSON to Bedrock geometry format.

    Args:
        agent: AssetConverterAgent instance
        model_path: Path to the model JSON file
        metadata: Optional metadata (texture_width, texture_height)
        entity_type: Type of model ("block", "item", "entity")
        model_cache: Optional cache of model path -> JSON data for parent resolution
        namespace: Optional namespace for resolving parent model paths

    Returns:
        Dict with conversion result
    """
    warnings = []
    try:
        model_p = Path(model_path)
        model_cache = model_cache or {}

        if model_p.exists():
            with open(model_p, "r") as f:
                java_model = json.load(f)
        elif model_path in model_cache:
            java_model = model_cache[model_path]
        else:
            raise FileNotFoundError(f"Model file not found: {model_path}")

        bedrock_identifier = f"geometry.{entity_type}.{model_p.stem}"
        texture_width = metadata.get("texture_width", 16)
        texture_height = metadata.get("texture_height", 16)

        bedrock_geo = {
            "format_version": "1.12.0",
            "minecraft:geometry": [
                {
                    "description": {
                        "identifier": bedrock_identifier,
                        "texture_width": texture_width,
                        "texture_height": texture_height,
                        "visible_bounds_width": 2,
                        "visible_bounds_height": 2,
                        "visible_bounds_offset": [0, 0.5

*[truncated — see source for full prompt]*