# Feature Extractor

> """
AST-based and bytecode-based feature extraction for Java mods
"""

import re
from pathlib import Path
from typing import List, Dict, Any, Optional

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
AST-based and bytecode-based feature extraction for Java mods
"""

import re
from pathlib import Path
from typing import List, Dict, Any, Optional

from utils.logging_config import get_agent_logger

logger = get_agent_logger("java_analyzer.feature_extractor")

try:
    import tree_sitter_java as ts_java
    from tree_sitter import Language, Parser

    TREE_SITTER_AVAILABLE = True
except ImportError:
    TREE_SITTER_AVAILABLE = False
    ts_java = None
    Parser = None

try:
    import javassist

    JAVASSIST_AVAILABLE = True
except ImportError:
    javassist = None
    JAVASSIST_AVAILABLE = False


FEATURE_ANALYSIS_FILE_LIMIT = 10
METADATA_AST_FILE_LIMIT = 5
DEPENDENCY_ANALYSIS_FILE_LIMIT = 10


class FeatureExtractor:
    """Extracts mod features from Java AST and bytecode"""

    def __init__(self, feature_patterns: Dict[str, List[str]]):
        self.feature_patterns = feature_patterns
        self._ts_parser = None

    def extract_features_from_ast(self, tree: Dict) -> Dict:
        """Extract features from parsed Java AST (tree-sitter format)."""
        features = {
            "blocks": [],
            "items": [],
            "entities": [],
            "recipes": [],
            "dimensions": [],
            "gui": [],
            "machinery": [],
            "commands": [],
            "events": [],
            "tile_entities": [],
        }

        try:
            classes = self._find_nodes_by_type(tree, "class_declaration")

            for class_node in classes:
                class_info = self._extract_class_info_from_ts(class_node)
                class_name = class_info.get("name", "")
                superclass = class_info.get("superclass", "")

                is_block_entity = "BlockEntity" in superclass

                if is_block_entity:
                    tile_info = {
                        "name": class_name,
                        "registry_name": _class_name_to_registry_name(class_name),
                        "methods": cl

*[truncated — see source for full prompt]*