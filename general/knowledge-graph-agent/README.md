# Knowledge Graph Agent

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
from typing import TYPE_CHECKING, Optional, Union

if TYPE_CHECKING:
    from unstructured.documents.elements import Element

from camel.agents import ChatAgent
from camel.messages import BaseMessage
from camel.models import BaseModelBackend
from camel.prompts import TextPrompt
from camel.storages.graph_storages.graph_element import (
    GraphElement,
    Node,
    Relationship,
)
from camel.types import RoleType

# AgentOps decorator setting
try:
    import os

    if os.getenv("AGENTOPS_API_KEY") is not None:
        from agentops import track_agent
    else:
        raise ImportError
except (ImportError, AttributeError):
    from camel.utils import track_agent


text_prompt = """
You are tasked with extracting nodes and relationships from given content and
structures them into Node and Relationship objects. Here's the outline of what
you needs to do:

Content Extraction:
You should be able to process input content and identify entities mentioned
within it.
Entities can be any noun phrases or concepts that represent distinct entities
in the context of the given content.

Node Extraction:
For each identified entity, you should create a Node object.
Each Node object should have a unique identifier (id) and a type (type).
Additional properties associated with the node can also 

*[truncated — see source for full prompt]*