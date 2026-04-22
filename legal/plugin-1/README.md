# Plugin

> clawarena plugins are `.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# clawarena Plugin System

clawarena plugins are `.py` files that register external framework adapters, enabling `--framework` to reference frameworks defined outside the core codebase.

## Overview

The plugin system serves one purpose: **extending clawarena with new framework adapters**. Each plugin file is a Python script that calls `register_adapter()` to make a new framework available.

Framework-specific inference hooks (post-round logic like feedback override, score override, early termination) are handled by the **engine's `on_round_complete()` method**, not by plugins.

## Writing a Plugin

A plugin file registers one or more adapters:

```python
# my_framework.py
from clawarena.adapters.registry import register_adapter
from clawarena.adapters.base import FrameworkAdapter
from clawarena.engines.base import AgentEngine
from clawarena.data_handlers.base import DataHandler
from clawarena.core.types import AgentResult, WorkCopy

class MyEngine(AgentEngine):
    async def run_agent(self, session_id, message, work_copy, **kwargs):
        # ... your framework invocation logic ...
        return AgentResult(status="success", answer="...")

class MyDataHandler(DataHandler):
    # ... implement all abstract methods ...
    pass

register_adapter("my_framework", lambda: FrameworkAdapter(
    name="my_framework",
    engine=MyEngine(),
    data_handler=MyDataHandler(),
))
```

## CLI Usage

```bash
# Load plugin and use the registered framework
clawarena infer --data tests.json --framework my_framework --out results/ \
    --plugin my_framework.py

# Multiple plugins
clawarena run --data tests.json --frameworks openclaw,my_framework --out results/ \
    --plugin my_framework.py another_plugin.py
```

The `--plugin` flag is available on `infer` and `run` commands. Plugin files are executed before the framework is resolved, so any adapter registered during loading is immediately available.

## Engine Round Hooks

Post-round logic (previously handled by the old plugin/ca

*[truncated — see source for full prompt]*