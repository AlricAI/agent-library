# Jar Extractor

> """
JAR texture extraction module.
"""

import logging
import zipfile
from pathlib import Path
from typing import Dict, List

logger = logging.getLogg

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
JAR texture extraction module.
"""

import logging
import zipfile
from pathlib import Path
from typing import Dict, List

logger = logging.getLogger(__name__)


def extract_textures_from_jar(self, jar_path: str, output_dir: str, namespace: str = None) -> Dict:
    """
    Extract all textures from a Java mod JAR file.

    Args:
        jar_path: Path to the JAR file
        output_dir: Directory to extract textures to
        namespace: Optional namespace to filter textures (e.g., 'simple_copper')

    Returns:
        Dict with extraction results including list of extracted textures
    """
    extracted_textures = []
    errors = []
    warnings = []

    try:
        jar_path_obj = Path(jar_path)
        if not jar_path_obj.exists():
            return {
                "success": False,
                "error": f"JAR file not found: {jar_path}",
                "extracted_textures": [],
            }

        output_path = Path(output_dir)
        output_path.mkdir(parents=True, exist_ok=True)

        with zipfile.ZipFile(jar_path, "r") as jar:
            file_list = jar.namelist()

            texture_files = [
                f
                for f in file_list
                if f.startswith("assets/") and "/textures/" in f and f.endswith(".png")
            ]

            if namespace:
                texture_files = [f for f in texture_files if f.startswith(f"assets/{namespace}/")]

            mcmeta_files = [
                f
                for f in file_list
                if f.startswith("assets/") and "/textures/" in f and f.endswith(".png.mcmeta")
            ]

            for texture_file in texture_files:
                try:
                    texture_data = jar.read(texture_file)

                    bedrock_path = agent._map_java_texture_to_bedrock(texture_file)

                    full_output_dir = output_path / Path(bedrock_path).parent
                    full_output_dir.mkdir(parents=True, exist_ok=True)

                    out

*[truncated — see source for full prompt]*