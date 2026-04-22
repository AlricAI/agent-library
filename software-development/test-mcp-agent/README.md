# Test Mcp Agent

> # Licensed under the Apache License, Version 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ========= Copyright 2023-2026 @ CAMEL-AI.org. All Rights Reserved. =========
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
# ========= Copyright 2023-2026 @ CAMEL-AI.org. All Rights Reserved. =========

from typing import List

import pytest

from camel.parsers.mcp_tool_call_parser import extract_tool_calls_from_text


@pytest.mark.parametrize(
    "content,expected",
    [
        (
            """Here is the call:
```json
{
  \"server_idx\": 0,
  \"tool_name\": \"search_tool\",
  \"tool_args\": {\"query\": \"hello\"}
}
```
""",
            [
                {
                    "server_idx": 0,
                    "tool_name": "search_tool",
                    "tool_args": {"query": "hello"},
                }
            ],
        ),
        (
            """Please run this: {\"server_idx\": 1, \"tool_name\": \"math\",
            \"tool_args\": {\"a\": 1, \"b\": 2}}""",
            [
                {
                    "server_idx": 1,
                    "tool_name": "math",
                    "tool_args": {"a": 1, "b": 2},
                }
            ],
        ),
        (
            """Tool candidate {'server_idx': 0, 'tool_name': 'search',
            'tool_args': {'query': 'plan 2'}}""",
            [
                {
                    "server_idx": 0,
                    "tool_name": "search",
                    "tool_args": {"query": "plan 2"},
                }
            ],
        ),
        (
            """Multiple calls: [{\"server_idx\": 0, \"

*[truncated — see source for full prompt]*