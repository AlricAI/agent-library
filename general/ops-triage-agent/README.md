# Ops Triage Agent

> """Reference agent for operations triage tasks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Reference agent for operations triage tasks."""

from __future__ import annotations


class OpsTriageAgent:
    def __init__(self) -> None:
        self.reset({})

    def reset(self, task_spec):
        self.task_spec = task_spec or {}
        self.obs = None
        self.target_key: str | None = None
        self.files: list[str] = []
        self.seen_paths: set[str] = set()
        self.pending_extract_key: str | None = None
        self.desired_config: dict[str, str] | None = None
        self.live_config: dict[str, str] | None = None

    def observe(self, observation):
        self.obs = observation

    def _parse_config(self, content: str) -> dict[str, str]:
        data: dict[str, str] = {}
        for line in content.splitlines():
            if "=" not in line:
                continue
            key, value = line.split("=", 1)
            data[key.strip()] = value.strip()
        return data

    def _record_readme(self, content: str) -> None:
        for line in content.splitlines():
            if line.startswith("TARGET_KEY="):
                self.target_key = line.split("=", 1)[1].strip()
                break

    def _queue_files(self, files: list[str]) -> None:
        ordered = sorted(files)
        self.files = [path for path in ordered if path not in self.seen_paths]

    def _next_file(self) -> str | None:
        while self.files:
            candidate = self.files.pop(0)
            if candidate not in self.seen_paths:
                self.seen_paths.add(candidate)
                return candidate
        return None

    def _maybe_emit_patch(self):
        if self.target_key != "DRIFT_PATCH":
            return None
        if not self.desired_config or not self.live_config:
            return None
        for key, desired in self.desired_config.items():
            if self.live_config.get(key) != desired:
                patch = f"{key}={desired}"
                return {"type": "set_output", "args": {"key": self.target_key, "value"

*[truncated — see source for full prompt]*