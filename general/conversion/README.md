# Conversion

> """
Core texture conversion module.
"""

import json
import logging
from pathlib import Path
from typing import Dict, List

from PIL import Image

log

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Core texture conversion module.
"""

import json
import logging
from pathlib import Path
from typing import Dict, List

from PIL import Image

logger = logging.getLogger(__name__)


def _convert_single_texture(
    self, texture_path: str, metadata: Dict, usage: str, output_dir: Path = None
) -> Dict:
    """
    Convert a single texture file to Bedrock format with enhanced validation and optimization.
    If output_dir is provided, saves the converted texture to disk.
    """
    cache_key = f"{texture_path}_{usage}_{hash(str(metadata))}"

    if cache_key in agent._conversion_cache:
        logger.debug(f"Using cached result for texture conversion: {texture_path}")
        return agent._conversion_cache[cache_key]

    try:
        if not Path(texture_path).exists():
            logger.warning(f"Texture file not found: {texture_path}. Generating fallback texture.")
            img = agent._generate_fallback_texture(usage)
            original_dimensions = img.size
            is_valid_png = False
            optimizations_applied = ["Generated fallback texture"]
        else:
            try:
                img = Image.open(texture_path)
                original_dimensions = img.size

                is_valid_png = img.format == "PNG"

                img = img.convert("RGBA")
                optimizations_applied = ["Converted to RGBA"] if not is_valid_png else []
            except Exception as open_error:
                logger.warning(
                    f"Failed to open texture {texture_path}: {open_error}. Generating fallback texture."
                )
                img = agent._generate_fallback_texture(usage)
                original_dimensions = img.size
                is_valid_png = False
                optimizations_applied = ["Generated fallback texture due to open error"]

        width, height = img.size
        resized = False

        max_res = agent.texture_constraints.get("max_resolution", 1024)
        must_be_power_of_2 = agent.textu

*[truncated — see source for full prompt]*