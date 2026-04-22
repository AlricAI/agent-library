# Runbook Verifier Agent

> """Reference agent for the runbook_verifier task.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Reference agent for the runbook_verifier task."""

from __future__ import annotations

from typing import Dict, List, Optional

from tasks.runbook_verifier.shared import (
    HANDOFF_PATH,
    README_PATH,
    RUNBOOK_INDEX_PATH,
    SEQUENCE_PATH,
    TIMELINE_PATH,
)


class RunbookState:
    def __init__(self) -> None:
        self.target_key: Optional[str] = None
        self.phase_paths: List[str] = []
        self.phase_codes: Dict[str, str] = {}
        self.ack_id: Optional[str] = None
        self.handoff_token: Optional[str] = None
        self.read_files: set[str] = set()
        self.listed: bool = False


class RunbookVerifierAgent:
    """Deterministic agent that stitches runbook artifacts into a checksum."""

    def __init__(self) -> None:
        self.reset({})

    def reset(self, task_spec):
        self.task_spec = task_spec or {}
        self.obs = None
        self.state = RunbookState()
        self._last_checksum: Optional[str] = None

    def observe(self, observation):
        self.obs = observation

    # --------------------- parsing helpers ---------------------
    def _parse_lines(self, content: str) -> dict[str, str]:
        data: dict[str, str] = {}
        for line in content.splitlines():
            if "=" not in line:
                continue
            key, value = line.split("=", 1)
            data[key.strip()] = value.strip()
        return data

    def _handle_read(self, path: str, content: str) -> None:
        self.state.read_files.add(path)
        data = self._parse_lines(content)
        if path == README_PATH:
            target = data.get("TARGET_KEY")
            if target:
                self.state.target_key = target
        elif path == RUNBOOK_INDEX_PATH:
            indexed = []
            for idx in range(1, 10):
                path_key = f"PHASE_{idx}_PATH"
                if path_key not in data:
                    break
                indexed.append(data[path_key])
            if indexed:
       

*[truncated — see source for full prompt]*