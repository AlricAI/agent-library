# Url Open Agent

> import asyncio
import base64
import io
import json
import os
import pathlib
import re

import aiohttp
import aiohttp.client_exceptions
import bs4
impo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import base64
import io
import json
import os
import pathlib
import re

import aiohttp
import aiohttp.client_exceptions
import bs4
import google.auth.transport.requests
import google.oauth2.credentials
import google_auth_httplib2
import googleapiclient.discovery
import googleapiclient.errors
import googleapiclient.http
import httplib2
import opentelemetry.context
import opentelemetry.trace
import playwright.async_api
import slack_sdk.errors
import slack_sdk.web.async_client
import tiktoken
import unstructured.partition.auto

import cortex.exceptions
import cortex.llm.openai.agent.browser_agent
import cortex.llm.openai.model


class URLOpenAgent(cortex.llm.openai.agent.Agent):
    browser: playwright.async_api.Browser
    github_token: str
    slack_token: str
    google_credentials: google.oauth2.credentials.Credentials

    def __init__(
        self,
        browser: playwright.async_api.Browser,
        github_token: str,
        slack_token: str,
        google_credentials: google.oauth2.credentials.Credentials,
        model: cortex.llm.openai.model.CompletionModel,
        encoder: tiktoken.Encoding,
    ):
        self.browser = browser
        self.github_token = github_token
        self.slack_token = slack_token
        self.google_credentials = google_credentials

        self.model = model
        self.encoder = encoder
        self.system_prompt = "Your task is to choice the correct function to open the URL and retrieve its content."
        self.functions = {
            "open_github_file": cortex.llm.openai.agent.FunctionDefinition(
                func=self.open_github_file,
                cache=cortex.llm.openai.agent.FunctionCache(
                    enabled=True, similarity_threshold=1.0
                ),
                direct_return=True,
                description="Open the GitHub file URL and retrieve its content. e.g. https://github.com/torvalds/linux/blob/master/net/ipv4/tcp.c -> owner: torvalds, repo: linux, ref: master, 

*[truncated — see source for full prompt]*