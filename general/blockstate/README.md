# Blockstate

> """
Blockstate parsing and conversion module.
"""

import json
import logging
from pathlib import Path
from typing import Dict, List, Optional

logger

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Blockstate parsing and conversion module.
"""

import json
import logging
from pathlib import Path
from typing import Dict, List, Optional

logger = logging.getLogger(__name__)


def parse_blockstate(blockstate_data: Dict) -> Dict:
    """
    Parse a Java blockstate JSON and extract all model variants.

    Blockstates come in two formats:
    1. variants: { "variant_name": { "model": "modid:path/to/model", "y": 90, ... }, ... }
    2. multipart: [ { "when": { "condition": value }, "apply": { "model": "..." } }, ... ]

    Args:
        blockstate_data: Parsed blockstate JSON

    Returns:
        Dict with model variants and their properties
    """
    variants = blockstate_data.get("variants", {})
    multipart = blockstate_data.get("multipart", [])

    parsed_variants = []

    for variant_name, variant_props in variants.items():
        if isinstance(variant_props, dict):
            model_path = variant_props.get("model", "")
            y_rotation = variant_props.get("y", 0)
            x_rotation = variant_props.get("x", 0)
            uvlock = variant_props.get("uvlock", False)

            parsed_variants.append(
                {
                    "variant_key": variant_name,
                    "model": model_path,
                    "y_rotation": y_rotation,
                    "x_rotation": x_rotation,
                    "uvlock": uvlock,
                    "type": "variant",
                }
            )

    for part in multipart:
        when = part.get("when", {})
        apply_props = part.get("apply", {})

        model_path = apply_props.get("model", "")
        y_rotation = apply_props.get("y", 0)
        x_rotation = apply_props.get("x", 0)
        uvlock = apply_props.get("uvlock", False)

        parsed_variants.append(
            {
                "variant_key": json.dumps(when),
                "model": model_path,
                "y_rotation": y_rotation,
                "x_rotation": x_rotation,
                "uvlock": uv

*[truncated — see source for full prompt]*