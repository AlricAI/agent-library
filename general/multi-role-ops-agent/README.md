# Multi Role Ops Agent

> """Sample multi-agent orchestrated agent for TraceCore tasks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Sample multi-agent orchestrated agent for TraceCore tasks."""

from __future__ import annotations

from typing import Any

from agent_bench.agents.multi_agent_orchestrator import (
    MultiAgentOrchestrator,
    OrchestrationPlan,
    RoleContract,
    RosterEntry,
)


class _ReconAgent:
    """Scans README + directory structure to prime shared context."""

    def __init__(self, board: dict[str, Any]):
        self._board = board
        self._observation: dict | None = None

    def reset(self, _task_spec: dict | None) -> None:
        self._observation = None

    def observe(self, observation: dict | None) -> None:
        self._observation = observation
        if not observation:
            return
        last_action = observation.get("last_action") or {}
        last_result = observation.get("last_action_result") or {}
        if not last_result.get("ok"):
            return

        if last_action.get("type") == "read_file" and last_action.get("args", {}).get("path") == "/app/README.md":
            content = last_result.get("content", "")
            for line in content.splitlines():
                if line.startswith("TARGET_KEY="):
                    self._board["target_key"] = line.split("=", 1)[1].strip()
                    break
            signal_paths: list[str] = []
            for line in content.splitlines():
                stripped = line.strip()
                if stripped.startswith("- /"):
                    candidate = stripped.lstrip("- ")
                    if candidate:
                        signal_paths.append(candidate)
            if signal_paths:
                self._board["signal_paths"] = signal_paths
                # Backwards compatibility for single-path scenarios.
                prioritized = None
                for path in signal_paths:
                    lowered = path.lower()
                    if "incident" in lowered or lowered.endswith("manager_ack.txt"):
                        prioritized = path
        

*[truncated — see source for full prompt]*