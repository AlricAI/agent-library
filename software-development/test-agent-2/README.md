# Test Agent

> import os 
import unittest
from evoagentx.models.litellm_model import LiteLLM
from evoagentx.models.model_configs import LiteLLMConfig
from evoagentx.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import os 
import unittest
from evoagentx.models.litellm_model import LiteLLM
from evoagentx.models.model_configs import LiteLLMConfig
from evoagentx.agents.agent import Agent
from evoagentx.actions.action import Action


class TestModule(unittest.TestCase):

    def setUp(self):
        self.save_file = "tests/agents/saved_agent.json"

    def test_initialization(self):

        agent_data = {
            "name": "test_agent", 
            "description": "test_agent_description", 
            "llm_config": {
                "class_name": "LiteLLMConfig",
                "model": "gpt-4o-mini", 
                "openai_key": "xxxxx"
            }, 
            "actions": [
                {
                    "class_name": "Action", 
                    "name": "test_action_name", 
                    "description": "test_action_desc", 
                    "prompt": "test_action_prompt", 
                }
            ]
        }
        agent = Agent.from_dict(agent_data)
        self.assertEqual(agent.llm_config.model, "gpt-4o-mini")
        self.assertTrue(isinstance(agent.llm, LiteLLM))
        self.assertTrue(isinstance(agent.actions[0], Action))

        # test actions
        self.assertTrue(len(agent.get_all_actions()) == 1)
        action = agent.get_action("test_action_name")
        self.assertEqual(action.name, "test_action_name") 
        self.assertEqual(action.description, "test_action_desc") 

        # test get_prompts and set_prompts 
        prompts = agent.get_prompts() 
        self.assertEqual(len(prompts), 1)
        self.assertEqual(prompts["test_action_name"]["system_prompt"], None) 
        self.assertEqual(prompts["test_action_name"]["prompt"], "test_action_prompt")

        agent.set_prompt("test_action_name", "new_test_action_prompt", "new_system_prompt") 
        self.assertTrue(agent.system_prompt, "new_system_prompt")
        self.assertEqual(agent.get_action("test_action_name").prompt, "new_test_action_prompt")

        agent.set_pr

*[truncated — see source for full prompt]*