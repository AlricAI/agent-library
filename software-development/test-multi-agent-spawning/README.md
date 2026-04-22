# Test Multi Agent Spawning

> """Integration tests for MultiAgentLearningAgent with spawning.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Integration tests for MultiAgentLearningAgent with spawning.

Tests:
- MultiAgentLearningAgent with enable_spawning=True
- Multi-hop question triggers spawning
- Code generation specialist for problem-solving
- Backward compatibility (enable_spawning=False)
- GoalSeekingAgent base class spawning integration
"""

from __future__ import annotations

from amplihack.agents.goal_seeking.sdk_adapters.base import (
    AgentResult,
    AgentTool,
    GoalSeekingAgent,
    SDKType,
)
from amplihack.agents.goal_seeking.sub_agents.agent_spawner import (
    AgentSpawner,
)
from amplihack.agents.goal_seeking.sub_agents.coordinator import (
    CoordinatorAgent,
)
from amplihack.agents.goal_seeking.sub_agents.tool_injector import (
    inject_sdk_tools,
)

# ============================================================
# Minimal GoalSeekingAgent for testing
# ============================================================


class MinimalAgent(GoalSeekingAgent):
    """Minimal concrete implementation for testing base class features."""

    def _create_sdk_agent(self) -> None:
        self._sdk_agent = "mock"

    async def _run_sdk_agent(self, task: str, max_turns: int = 10) -> AgentResult:
        return AgentResult(response=f"Ran: {task}", goal_achieved=True)

    def _get_native_tools(self) -> list[str]:
        return ["test_tool"]

    def _register_tool_with_sdk(self, tool: AgentTool) -> None:
        # Actually add the tool to _tools so injection tests can verify
        self._tools.append(tool)


# ============================================================
# GoalSeekingAgent Base Class Spawning Tests
# ============================================================


class TestGoalSeekingAgentSpawning:
    """Tests for spawning integration in GoalSeekingAgent base."""

    def test_spawning_disabled_by_default(self, tmp_path):
        """Spawning is disabled by default."""
        agent = MinimalAgent(
            name="test_agent",
            storage_path=tmp_path / "ag

*[truncated — see source for full prompt]*