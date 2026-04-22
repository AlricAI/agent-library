# Atlas

> """
Atlas detection and extraction module.
"""

import json
import logging
import zipfile
from pathlib import Path
from typing import Dict, List, Opti

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Atlas detection and extraction module.
"""

import json
import logging
import zipfile
from pathlib import Path
from typing import Dict, List, Optional

from PIL import Image

logger = logging.getLogger(__name__)


def detect_texture_atlas(agent, texture_path: str) -> Dict:
    """
    Detect if a texture is a texture atlas (combined multiple textures).

    Args:
        texture_path: Path to the texture file

    Returns:
        Dict with atlas detection results
    """
    try:
        path = Path(texture_path)
        if not path.exists():
            return {"is_atlas": False, "error": "File not found"}

        img = Image.open(texture_path)
        width, height = img.size

        is_atlas = False
        atlas_type = None
        tile_size = 16

        if width == height and width > 16:
            if width >= 64:
                is_atlas = True
                atlas_type = "grid"
                tile_size = 16

        common_atlas_sizes = [256, 512, 1024]
        if width in common_atlas_sizes or height in common_atlas_sizes:
            is_atlas = True
            atlas_type = "grid"

        if width != height and (width % 16 == 0 or height % 16 == 0):
            if width >= 64 or height >= 64:
                is_atlas = True
                atlas_type = "strip"

        tiles_x = width // tile_size if tile_size > 0 else 1
        tiles_y = height // tile_size if tile_size > 0 else 1

        return {
            "is_atlas": is_atlas,
            "atlas_type": atlas_type,
            "width": width,
            "height": height,
            "tile_size": tile_size,
            "tiles_x": tiles_x,
            "tiles_y": tiles_y,
            "total_tiles": tiles_x * tiles_y if is_atlas else 1,
        }

    except Exception as e:
        logger.error(f"Error detecting texture atlas: {e}")
        return {"is_atlas": False, "error": str(e)}


def extract_texture_atlas(
    self,
    atlas_path: str,
    output_dir: str,
    tile_size: int = 16,
    n

*[truncated — see source for full prompt]*