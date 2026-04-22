# Naive Llm Agent

> """Naive single-shot LLM loop baseline agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Naive single-shot LLM loop baseline agent."""

from __future__ import annotations


class NaiveLLMLoopAgent:
    """Extremely simple agent that peeks once and retries a single time."""

    def __init__(self) -> None:
        self.reset({})

    def reset(self, task_spec):  # noqa: D401 - minimal baseline
        self.task_spec = task_spec or {}
        self.obs = None
        self.files: list[str] = []
        self.file_index = 0
        self.cached_content: str | None = None
        self.extracted_value: str | None = None
        self.retry_budget = 1
        task_id = self.task_spec.get("id")
        self.output_key = "API_KEY" if task_id == "filesystem_hidden_config" else "ACCESS_TOKEN"
        self.root = "/app"

    def observe(self, observation):
        self.obs = observation

    def _remember_listing(self, result: dict) -> None:
        files = result.get("files")
        if isinstance(files, list):
            self.files = [str(path) for path in files]
            self.file_index = 0

    def _next_path(self) -> str | None:
        if self.file_index < len(self.files):
            path = self.files[self.file_index]
            self.file_index += 1
            return path
        return None

    def act(self) -> dict:
        last_action = self.obs.get("last_action") if self.obs else None
        last_result = self.obs.get("last_action_result") if self.obs else None

        if last_action and last_result:
            action_type = last_action.get("type")
            if action_type == "list_dir" and last_result.get("ok"):
                self._remember_listing(last_result)
            elif action_type == "read_file" and last_result.get("ok"):
                self.cached_content = last_result.get("content")
            elif action_type == "extract_value" and last_result.get("ok"):
                self.extracted_value = last_result.get("value")
            elif action_type == "set_output" and last_result.get("ok"):
                return {"type": "wait",

*[truncated — see source for full prompt]*