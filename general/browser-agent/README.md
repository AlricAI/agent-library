# Browser Agent

> import bs4
import playwright.async_api
import tiktoken

import cortex.llm.openai.agent
import cortex.llm.openai.model


class BrowserAgent(cortex.llm.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import bs4
import playwright.async_api
import tiktoken

import cortex.llm.openai.agent
import cortex.llm.openai.model


class BrowserAgent(cortex.llm.openai.agent.Agent):
    browser: playwright.async_api.Browser
    page: playwright.async_api.Page | None

    def __init__(
        self,
        browser: playwright.async_api.Browser,
        model: cortex.llm.openai.model.CompletionModel,
        encoder: tiktoken.Encoding,
    ):
        self.browser = browser
        self.page = None

        self.model = model
        self.encoder = encoder
        self.functions = {
            "navigate": cortex.llm.openai.agent.FunctionDefinition(
                func=self.navigate,
                description="Navigate a browser to the specified URL.",
                parameters={
                    "type": "object",
                    "properties": {
                        "url": {
                            "type": "string",
                            "description": "url to navigate to",
                        },
                    },
                    "required": ["url"],
                },
            ),
            "navigate_back": cortex.llm.openai.agent.FunctionDefinition(
                func=self.navigate_back,
                description="Navigate back to the previous page in the browser history.",
                parameters={
                    "type": "object",
                    "properties": {},
                },
            ),
            "extract_text": cortex.llm.openai.agent.FunctionDefinition(
                func=self.extract_text,
                direct_return=True,  # Prompt be duplicated if without planner
                description="Extract all the text on the current web page.",
                parameters={
                    "type": "object",
                    "properties": {},
                },
            ),
            "screenshot": cortex.llm.openai.agent.FunctionDefinition(
                func=self.screenshot,
                d

*[truncated — see source for full prompt]*