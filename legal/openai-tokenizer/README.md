# Openai Tokenizer

> #
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtai

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Copyright 2025 Dimensional Inc.
#
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

import tiktoken
from dimos.agents.tokenizer.base import AbstractTokenizer
from dimos.utils.logging_config import setup_logger

class OpenAITokenizer(AbstractTokenizer):

    def __init__(self, model_name: str = "gpt-4o", **kwargs):
        super().__init__(**kwargs)

        # Initilize the tokenizer for the openai set of models
        self.model_name = model_name
        try:
            self.tokenizer = tiktoken.encoding_for_model(self.model_name)
        except Exception as e:
            raise ValueError(
                f"Failed to initialize tokenizer for model {self.model_name}. Error: {str(e)}"
            )

    def tokenize_text(self, text):
        """
        Tokenize a text string using the openai tokenizer.
        """
        return self.tokenizer.encode(text)

    def detokenize_text(self, tokenized_text):
        """
        Detokenize a text string using the openai tokenizer.
        """
        try:
            return self.tokenizer.decode(tokenized_text, errors="ignore")
        except Exception as e:
            raise ValueError(f"Failed to detokenize text. Error: {str(e)}")

    def token_count(self, text):
        """
        Gets the token count of a text string using the openai tokenizer.
        """
        return len(self.tokenize_text(text)) if text else 0

    @staticmethod
    def image_token_count(image_width, image_height, image_detail="high"):
        """
       

*[truncated — see source for full prompt]*