# Chain Agent

> """Chain-aware reference agent for rate_limited_chain@1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Chain-aware reference agent for rate_limited_chain@1."""

from __future__ import annotations


class ChainAgent:
    def __init__(self) -> None:
        self.reset({})

    def reset(self, task_spec):
        self.task_spec = task_spec
        self.payload_template: dict | None = None
        self.handshake_template: str | None = None
        self.handshake_id: str | None = None
        self.handshake_confirmed: bool = False
        self.pending_wait: int = 0
        self.cached_token: str | None = None
        self.output_committed = False
        self.output_key: str = task_spec.get("output_key", "ACCESS_TOKEN")
        self.obs = None

    def observe(self, observation):
        self.obs = observation

    def _last(self):
        if not self.obs:
            return None, None, None
        action = self.obs.get("last_action")
        result = self.obs.get("last_action_result")
        action_type = action.get("type") if isinstance(action, dict) else None
        return action, result, action_type

    def _call(self, endpoint: str, payload: dict | None = None) -> dict:
        return {"type": "call_api", "args": {"endpoint": endpoint, "payload": payload}}

    def _handshake_phrase(self) -> str:
        if not self.handshake_template or not self.handshake_id:
            return ""
        filled = self.handshake_template.replace("<handshake_id>", self.handshake_id)

        marker = "respond with:"
        lower_filled = filled.lower()
        start_index = lower_filled.find(marker)
        if start_index != -1:
            phrase = filled[start_index + len(marker) :]
        else:
            phrase = filled

        for separator in ("\n", "\r"):
            sep_index = phrase.find(separator)
            if sep_index != -1:
                phrase = phrase[:sep_index]
                break

        return phrase.strip().strip(". ")

    def _call_token(self) -> dict:
        if self.payload_template is None:
            return {"type": "get_required_payload"

*[truncated — see source for full prompt]*