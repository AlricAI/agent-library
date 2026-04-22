# Test Repo Agent

> # Licensed under the Apache License, Version 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ========= Copyright 2023-2024 @ CAMEL-AI.org. All Rights Reserved. =========
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ========= Copyright 2023-2024 @ CAMEL-AI.org. All Rights Reserved. =========

import sys
from unittest.mock import MagicMock, patch

import pytest

from camel.agents.repo_agent import (
    GitHubFile,
    ProcessingMode,
    RepoAgent,
    RepositoryInfo,
)
from camel.messages import BaseMessage
from camel.models import BaseModelBackend
from camel.responses import ChatAgentResponse
from camel.types import ModelType

# Create mock Github module
mock_github_module = MagicMock()
mock_github_class = MagicMock()
mock_github_module.Github = mock_github_class
sys.modules['github'] = mock_github_module

# Mock for ModelFactory
mock_model = MagicMock()
mock_model.token_counter.count_tokens_from_messages.return_value = 100


class MockGithub:
    r"""Mock Github class for testing."""

    def __init__(self, *args, **kwargs):
        pass


class MockRepo:
    r"""Mock Repository class for testing."""

    def __init__(self, full_name, html_url):
        self.full_name = full_name
        self.html_url = html_url

    def get_contents(self, path):
        r"""Mock get_contents method."""
        if path == "":
            return [
                MockContent(
                    "file.py",
                    "file",
                    "https://github.com/test/repo/blob/main/file.py",
                )
            ]
        return MockContent(
            path, 

*[truncated — see source for full prompt]*