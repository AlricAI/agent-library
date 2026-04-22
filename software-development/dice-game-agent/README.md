# Dice Game Agent

> """
Deterministic dice game agent for testing record mode.
Uses seeded random to ensure deterministic behavior.
"""
import random


RANDOM_SEED = 42



## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Deterministic dice game agent for testing record mode.
Uses seeded random to ensure deterministic behavior.
"""
import random

# Seed for deterministic behavior
RANDOM_SEED = 42

class Agent:
    """TraceCore-compatible dice game agent using Pydantic AI."""

    def __init__(self, use_pydantic_ai=False):
        self.reset(None)
        self._use_pydantic_ai = use_pydantic_ai
        if use_pydantic_ai:
            from pydantic_ai import Agent as PydanticAgent
            self._pydantic_agent = PydanticAgent(
                'gateway/gemini:gemini-3-flash-preview',
                deps_type=str,
                instructions=(
                    "You're a dice game, you should roll the die and see if the number "
                    "you get back matches the user's guess. If so, tell them they're a winner. "
                    "Use the player's name in the response."
                ),
            )

    def reset(self, task_spec):
        """Reset agent state for new episode."""
        self.task = task_spec
        self.memory = {
            "roll_count": 0,
            "guesses": [],
            "results": [],
        }
        self.obs = None

    def observe(self, observation):
        """Receive observation from environment."""
        self.obs = observation

    def act(self):
        """Return action based on current observation."""
        # For record mode testing, we use deterministic dice rolls
        random.seed(RANDOM_SEED + self.memory["roll_count"])
        roll = random.randint(1, 6)
        self.memory["roll_count"] += 1

        return {
            "type": "roll_dice",
            "args": {"result": roll}
        }

# Standalone Pydantic AI version for direct testing
def run_standalone():
    """Run the dice game agent standalone."""
    from pydantic_ai import Agent as PydanticAgent, RunContext

    agent = PydanticAgent(
        'gateway/gemini:gemini-3-flash-preview',
        deps_type=str,
        instructions=(
            "You're a 

*[truncated — see source for full prompt]*