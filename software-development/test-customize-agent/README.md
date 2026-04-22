# Test Customize Agent

> import os 
import unittest
from unittest.mock import patch
from pydantic import Field 
from evoagentx.core.registry import register_parse_function 
fr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import os 
import unittest
from unittest.mock import patch
from pydantic import Field 
from evoagentx.core.registry import register_parse_function 
from evoagentx.models.model_configs import LiteLLMConfig
from evoagentx.agents.customize_agent import CustomizeAgent
from evoagentx.actions.action import ActionOutput
from evoagentx.core.message import Message, MessageType
from evoagentx.core.module_utils import extract_code_blocks

class CodeWriterActionOutput(ActionOutput):
    code: str = Field(description="The generated Python code") 

@register_parse_function
def customize_parse_func(content: str) -> dict:
    return {"code": extract_code_blocks(content)[0]}


class TestModule(unittest.TestCase):

    def setUp(self):
        self.save_files = [
            "tests/agents/saved_customize_agent.json", 
            "tests/agents/saved_customize_agent_with_inputs.json", 
            "tests/agents/saved_customize_agent_with_outputs.json",  
            "tests/agents/saved_customize_agent_with_inputs_outputs.json",
            "tests/agents/saved_customize_agent_with_parser.json" 
        ]

    @patch("evoagentx.models.litellm_model.LiteLLM.single_generate")
    def test_simple_agent(self, mock_generate):
        mock_generate.return_value = "Hello, world!"
        llm_config = LiteLLMConfig(model="gpt-4o-mini", openai_key="xxxxx")

        simple_agent = CustomizeAgent(
            name = "Simple Agent",
            description = "A simple agent that prints hello world", 
            prompt = "You are a simple agent that prints hello world.",
            llm_config = llm_config
        )
        self.assertEqual(simple_agent.name, "Simple Agent") 
        self.assertEqual(simple_agent.prompt, "You are a simple agent that prints hello world.")
        self.assertEqual(simple_agent.customize_action_name, "SimpleAgentAction") 
        self.assertEqual(simple_agent.get_prompts()["SimpleAgentAction"]["prompt"], "You are a simple agent that prints hello world.")
        self.

*[truncated — see source for full prompt]*