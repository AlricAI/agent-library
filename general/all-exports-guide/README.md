# ALL EXPORTS GUIDE

> ## Overview

This document describes the `__all__` exports pattern applied to 30 critical modules in AzureHayMaker, following the Bricks & Studs modul

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# __all__ Exports Guide

## Overview

This document describes the `__all__` exports pattern applied to 30 critical modules in AzureHayMaker, following the Bricks & Studs modular design philosophy.

## Philosophy

Every module in AzureHayMaker now clearly defines its public API through explicit `__all__` exports. This enables:

- **AI Regeneration**: Modules can be rebuilt from specifications alone
- **Clear Contracts**: Public APIs are explicitly documented
- **Better Import Control**: Only intended symbols are exported
- **Module Independence**: Each module is self-contained

## Pattern Applied

Each module follows this standard pattern:

```python
"""Module one-line description.

Philosophy:
- Single responsibility principle
- Self-contained and regeneratable
- Standard library only (when possible)
- [Other relevant philosophy points]

Public API (the "studs"):
    ClassName: Description of what this class does
    function_name: Description of what this function does
    CONSTANT_NAME: Description of this constant
"""

# ... module implementation ...

__all__ = ["ClassName", "function_name", "CONSTANT_NAME"]
```

## Modules Enhanced

The following 30 critical modules now have explicit `__all__` exports:

### Core Hooks (8 modules)
1. `hooks/power_steering_checker.py` - Power steering validation and checking
2. `hooks/stop.py` - Stop hook processing
3. `hooks/session_start.py` - Session initialization
4. `hooks/claude_power_steering.py` - Claude-specific power steering
5. `hooks/claude_reflection.py` - Claude reflection hook
6. `hooks/precommit_installer.py` - Pre-commit hook installation
7. `hooks/hook_processor.py` - Generic hook processing

### Security & Defense (2 modules)
8. `xpia_defense.py` - Cross-process injection attack defense
9. `context_preservation_secure.py` - Secure context preservation

### Remote Operations (4 modules)
10. `remote/cli.py` - Remote command-line interface
11. `remote/executor.py` - Remote execution engine
12. `remote/orchestrator.

*[truncated — see source for full prompt]*