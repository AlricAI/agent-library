# Archive Reader

> """
JAR/ZIP archive extraction for Java mod analysis
"""

import json
import zipfile
from pathlib import Path
from typing import List, Dict, Optional


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
JAR/ZIP archive extraction for Java mod analysis
"""

import json
import zipfile
from pathlib import Path
from typing import List, Dict, Optional

from utils.logging_config import get_agent_logger

logger = get_agent_logger("java_analyzer.archive_reader")


FEATURE_ANALYSIS_FILE_LIMIT = 10
METADATA_AST_FILE_LIMIT = 5
DEPENDENCY_ANALYSIS_FILE_LIMIT = 10


class ArchiveReader:
    """Handles JAR/ZIP extraction and analysis"""

    def __init__(self, feature_patterns: Dict[str, List[str]]):
        self.feature_patterns = feature_patterns

    def read_java_sources_from_jar(self, jar_path: str) -> List[tuple]:
        """Read all .java source files from a JAR.

        Returns:
            List of (name, code) tuples
        """
        sources = []
        try:
            with zipfile.ZipFile(jar_path, "r") as jar:
                for name in jar.namelist():
                    if name.endswith(".java"):
                        try:
                            code = jar.read(name).decode("utf-8", errors="replace")
                            sources.append((name, code))
                        except Exception as exc:
                            logger.warning(f"Skipping {name}: {exc}")
        except Exception as exc:
            logger.error(f"Cannot open JAR for chunking: {exc}")
        return sources

    def extract_mod_info_from_jar(self, jar: zipfile.ZipFile, file_list: list) -> dict:
        """Extract mod information from metadata files"""
        mod_info = {}

        if "fabric.mod.json" in file_list:
            try:
                content = jar.read("fabric.mod.json").decode("utf-8")
                fabric_data = json.loads(content)
                mod_info["name"] = fabric_data.get("id", fabric_data.get("name", "unknown")).lower()
                mod_info["version"] = fabric_data.get("version", "1.0.0")
                return mod_info
            except (json.JSONDecodeError, UnicodeDecodeError, KeyError) as e:
                logger.debug(f"Cou

*[truncated — see source for full prompt]*