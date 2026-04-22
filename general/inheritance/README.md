# Inheritance

> """
Model inheritance resolution module.
"""

import logging
from typing import Dict, List, Optional, Tuple

logger = logging.getLogger(__name__)


de

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Model inheritance resolution module.
"""

import logging
from typing import Dict, List, Optional, Tuple

logger = logging.getLogger(__name__)


def resolve_parent_model(
    model_data: Dict,
    model_cache: Dict[str, Dict],
    namespace: Optional[str] = None,
    _visited: Optional[set] = None,
) -> Tuple[List[Dict], List[str]]:
    """
    Recursively resolve parent model inheritance to get final elements.

    Java block models can have a "parent" that references another model.
    The parent model defines the base geometry (elements) that the child
    inherits and can override.

    Common parents:
    - block/cube (full block with 6 faces)
    - block/cube_all (block using single texture for all faces)
    - block/cube_column (log-like block with end and side textures)
    - block/cube_bottom_top (block with bottom, top, and side textures)
    - block/cube_directional (block with front/back/left/right/top/bottom)
    - item/generated (flat item sprite)
    - item/handheld (held item with depth)

    For Bedrock conversion, we need the resolved elements to convert.

    Args:
        model_data: The Java model JSON data
        model_cache: Cache of already-loaded models {model_path: model_data}
        namespace: Optional namespace for resolving model paths
        _visited: Internal set to track visited models (for cycle detection)

    Returns:
        Tuple of (resolved_elements, resolution_warnings)
    """
    if _visited is None:
        _visited = set()

    warnings: List[str] = []

    if "elements" in model_data:
        return model_data["elements"], warnings

    parent = model_data.get("parent")
    if not parent:
        warnings.append("Model has no elements and no parent - cannot resolve geometry")
        return [], warnings

    from agents.model_converter.blockstate import _resolve_parent_path

    resolved_parent = _resolve_parent_path(parent, namespace)

    if resolved_parent in _visited:
        warnings.append(f"Circular parent re

*[truncated — see source for full prompt]*