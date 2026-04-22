# Simple Reflection Spec

> ## Overview

Replace 22k lines with ~150 lines that achieve the same goal through delegation.

## Core Flow

```
Session ends → Read transcript → Dete

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Simple Reflection System Specification

## Overview

Replace 22k lines with ~150 lines that achieve the same goal through delegation.

## Core Flow

```
Session ends → Read transcript → Detect patterns → Create issue → Call UltraThink → Done
```

## Module Structure

### simple_reflection.py (~150 lines)

```python
#!/usr/bin/env python3
"""Simple reflection system that delegates to UltraThink."""

import os
import json
import subprocess
import re
from pathlib import Path
from typing import Optional, Dict, List

# Pattern definitions (20 lines)
PATTERNS = {
    "error_handling": r"(try:|except:|raise |Error\()",
    "type_hints": r"(def \w+\([^)]*\)\s*:(?!\s*->))",
    "docstrings": r'(def \w+.*:\n(?!\s*"""|\s*\'\'\'|\s*#))',
    "code_duplication": r"(# TODO: refactor|duplicate|copy-paste)",
    "complexity": r"(if.*if.*if|for.*for.*for)",
}

def read_transcript(path: Optional[str]) -> str:
    """Read session transcript."""
    if not path or not Path(path).exists():
        return ""
    return Path(path).read_text()

def detect_patterns(content: str) -> Dict[str, int]:
    """Detect improvement patterns."""
    results = {}
    for name, pattern in PATTERNS.items():
        matches = len(re.findall(pattern, content, re.MULTILINE))
        if matches > 0:
            results[name] = matches
    return results

def should_autofix() -> bool:
    """Check if auto-fix is enabled."""
    return os.getenv("ENABLE_AUTOFIX", "").lower() == "true"

def create_github_issue(patterns: Dict[str, int]) -> Optional[str]:
    """Create GitHub issue for top pattern."""
    if not patterns:
        return None

    # Simple priority: most occurrences wins
    top_pattern = max(patterns.items(), key=lambda x: x[1])
    pattern_name, count = top_pattern

    title = f"Improve {pattern_name.replace('_', ' ')}"
    body = f"""## Pattern Detected
- **Type**: {pattern_name}
- **Occurrences**: {count}

## Suggested Improvement
Refactor code to address {pattern_name.replace('_', ' ')} i

*[truncated — see source for full prompt]*