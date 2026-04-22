# Prebuilt Autonomous Agent

> """
Prebuilt Autonomous Agent.

A thin subclass of :class:`AutonomousAgent` that bootstraps its
``system_prompt.md`` and ``first_message.md`` from a r

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Prebuilt Autonomous Agent.

A thin subclass of :class:`AutonomousAgent` that bootstraps its
``system_prompt.md`` and ``first_message.md`` from a remote git repository
subfolder, copies user inputs into the workspace, and renders the first
message from a ``str.format`` template.

The main entry points are:

- :meth:`PrebuiltAutonomousAgent.run` — run to completion and return result.
- :meth:`PrebuiltAutonomousAgent.run_async` — async variant of ``run``.
- :meth:`PrebuiltAutonomousAgent.run_stream` — yield text chunks live.
- :meth:`PrebuiltAutonomousAgent.run_stream_async` — async variant of stream.
- :meth:`PrebuiltAutonomousAgent.run_console` — pretty terminal output with
  tool calls, results, and streamed text.
"""
from __future__ import annotations

import asyncio
import shutil
import string
import subprocess
import tempfile
from pathlib import Path
from typing import (
    Any,
    AsyncIterator,
    Dict,
    Iterator,
    List,
    Optional,
    Set,
    Union,
    TYPE_CHECKING,
)

from upsonic.agent.autonomous_agent.autonomous_agent import AutonomousAgent
from upsonic.agent.autonomous_agent.filesystem_toolkit import AutonomousFilesystemToolKit
from upsonic.agent.autonomous_agent.shell_toolkit import AutonomousShellToolKit

if TYPE_CHECKING:
    from upsonic.tasks.tasks import Task


class PrebuiltAutonomousAgent(AutonomousAgent):
    """
    Autonomous agent whose system prompt and first message come from a git repo.

    Constructor stores the repo coordinates; every call to :meth:`run`,
    :meth:`run_stream`, or :meth:`run_console` performs a fresh shallow
    ``git sparse-checkout`` of ``agent_folder`` into ``workspace``, so the
    workspace always reflects the current state of the remote template.

    ``workspace`` can be set either at construction time or per-run. If omitted
    at both, a :class:`ValueError` is raised when the agent is invoked.

    Example:
        ```python
        agent = PrebuiltAutonomousAgent(
            model="anthropic

*[truncated — see source for full prompt]*