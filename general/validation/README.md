# Validation

> """
Texture validation module.
"""

import logging
from pathlib import Path
from typing import Dict, List

from PIL import Image

logger = logging.get

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Texture validation module.
"""

import logging
from pathlib import Path
from typing import Dict, List

from PIL import Image

logger = logging.getLogger(__name__)


def validate_texture(agent, texture_path: str, metadata: Dict = None) -> Dict:
    """
    Validate a texture for Bedrock compatibility.

    Args:
        texture_path: Path to the texture file
        metadata: Optional metadata about the texture

    Returns:
        Dict with validation results
    """
    result = {"valid": True, "errors": [], "warnings": [], "properties": {}}

    try:
        path = Path(texture_path)

        if not path.exists():
            result["valid"] = False
            result["errors"].append(f"Texture file not found: {texture_path}")
            return result

        with Image.open(path) as img:
            width, height = img.size

            result["properties"] = {
                "width": width,
                "height": height,
                "format": img.format,
                "mode": img.mode,
                "size_bytes": path.stat().st_size,
            }

            if width != height:
                result["warnings"].append(f"Non-square texture: {width}x{height}")

            if not agent._is_power_of_2(width):
                result["warnings"].append(f"Width {width} is not a power of 2")
                if agent.texture_constraints.get("must_be_power_of_2", True):
                    result["valid"] = False
                    result["errors"].append(f"Width must be power of 2 for Bedrock")

            if not agent._is_power_of_2(height):
                result["warnings"].append(f"Height {height} is not a power of 2")
                if agent.texture_constraints.get("must_be_power_of_2", True):
                    result["valid"] = False
                    result["errors"].append(f"Height must be power of 2 for Bedrock")

            max_res = agent.texture_constraints.get("max_resolution", 1024)
            if width > max_res or height > m

*[truncated — see source for full prompt]*