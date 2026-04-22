# Jar Extractor

> """
Model extraction from JAR module.
"""

import json
import logging
import zipfile
from pathlib import Path
from typing import Dict, List, Optional


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Model extraction from JAR module.
"""

import json
import logging
import zipfile
from pathlib import Path
from typing import Dict, List, Optional

logger = logging.getLogger(__name__)


def extract_models_from_jar(
    jar_path: str, output_dir: str, namespace: Optional[str] = None
) -> Dict:
    """
    Extract all block/item/entity models from a Java mod JAR file.

    Java models are at: assets/<namespace>/models/block/<name>.json
                       assets/<namespace>/models/item/<name>.json
                       assets/<namespace>/models/entity/<name>.json

    Args:
        jar_path: Path to the JAR file
        output_dir: Directory to extract models to
        namespace: Optional namespace to filter models

    Returns:
        Dict with extraction results including list of extracted models
    """
    extracted_models = []
    errors = []
    warnings = []

    try:
        jar_path_obj = Path(jar_path)
        if not jar_path_obj.exists():
            return {
                "success": False,
                "error": f"JAR file not found: {jar_path}",
                "extracted_models": [],
            }

        output_path = Path(output_dir)
        output_path.mkdir(parents=True, exist_ok=True)

        with zipfile.ZipFile(jar_path, "r") as jar:
            file_list = jar.namelist()

            model_files = [
                f
                for f in file_list
                if f.startswith("assets/") and "/models/" in f and f.endswith(".json")
            ]

            if namespace:
                model_files = [f for f in model_files if f.startswith(f"assets/{namespace}/")]

            for model_file in model_files:
                try:
                    model_data = jar.read(model_file)
                    model_json = json.loads(model_data.decode("utf-8"))

                    parts = model_file.split("/")
                    if len(parts) >= 5:
                        model_namespace = parts[1]
                        model_type

*[truncated — see source for full prompt]*