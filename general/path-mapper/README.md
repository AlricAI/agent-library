# Path Mapper

> """
Java to Bedrock texture path mapping module.
"""

import logging
from pathlib import Path
from typing import Optional

logger = logging.getLogger(

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Java to Bedrock texture path mapping module.
"""

import logging
from pathlib import Path
from typing import Optional

logger = logging.getLogger(__name__)


def convert_java_texture_path(agent, java_path: str, bedrock_type: str = "blocks") -> str:
    """
    Convert Java texture path to Bedrock texture path.

    Args:
        java_path: Java texture path (e.g., 'assets/modid/textures/block/grass_block_side.png')
        bedrock_type: Target Bedrock texture type ('blocks', 'items', 'entity')

    Returns:
        Bedrock texture path (e.g., 'textures/blocks/grass_block_side')
    """
    parts = java_path.replace("\\", "/").split("/")

    try:
        textures_idx = parts.index("textures")
    except ValueError:
        textures_idx = -1

    if textures_idx >= 0:
        relative_parts = parts[textures_idx + 1 :]
    else:
        relative_parts = [p for p in parts if p.endswith(".png")]
        if relative_parts:
            relative_parts = [relative_parts[0]]
        else:
            relative_parts = []

    if relative_parts:
        filename = relative_parts[-1]
        if filename.endswith(".png"):
            filename = filename[:-4]
    else:
        filename = "unknown"

    bedrock_path = f"textures/{bedrock_type}/{filename}"

    logger.debug(f"Converted Java path '{java_path}' to Bedrock path '{bedrock_path}'")
    return bedrock_path


def _map_java_texture_to_bedrock(agent, java_path: str) -> str:
    """
    Map a Java mod texture path to Bedrock resource pack texture path.

    Java: assets/<namespace>/textures/<type>/<name>.png
    Bedrock: textures/<type>/<name>.png

    Args:
        java_path: Java mod texture path

    Returns:
        Bedrock texture path
    """
    parts = java_path.split("/")

    if len(parts) >= 5 and parts[0] == "assets" and parts[2] == "textures":
        texture_type = parts[3]
        texture_name = parts[4]

        bedrock_type = agent._map_texture_type(texture_type)

        return f"textures/{bedrock_type}

*[truncated — see source for full prompt]*