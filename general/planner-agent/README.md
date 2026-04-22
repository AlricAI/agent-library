# Planner Agent

> """Structured planner-style baseline agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Structured planner-style baseline agent."""

from __future__ import annotations


class StructuredPlannerAgent:
    """Maintains a simple plan queue and retries transient failures."""

    def __init__(self) -> None:
        self.reset({})

    def reset(self, task_spec):
        self.task_spec = task_spec or {}
        self.obs = None
        self.plan: list[dict] = []
        self.payload_template: dict | None = None
        self.handshake_template: str | None = None
        self.handshake_id: str | None = None
        self.pending_wait: int = 0
        self.cached_token: str | None = None
        self.output_committed = False
        self.output_key = self.task_spec.get("output_key", "ACCESS_TOKEN")

    def observe(self, observation):
        self.obs = observation

    def _schedule(self, action: dict) -> None:
        self.plan.append(action)

    def _next(self) -> dict | None:
        if self.plan:
            return self.plan.pop(0)
        return None

    def _ensure_handshake_plan(self):
        if not self.plan:
            self.plan.extend(
                [
                    {"type": "get_handshake_template", "args": {}},
                    {"type": "call_api", "args": {"endpoint": "/handshake"}},
                ]
            )

    def act(self) -> dict:
        last_action = self.obs.get("last_action") if self.obs else None
        last_result = self.obs.get("last_action_result") if self.obs else None
        action_type = last_action.get("type") if last_action else None

        if action_type == "get_required_payload" and last_result and last_result.get("ok"):
            self.payload_template = dict(last_result.get("payload_template", {}))

        if action_type == "get_handshake_template" and last_result and last_result.get("ok"):
            self.handshake_template = last_result.get("template")

        if action_type == "call_api" and last_result:
            endpoint = last_action.get("args", {}).get("endpoint") if last_action else No

*[truncated — see source for full prompt]*