# Root Agent

> import asyncio
import collections.abc
import datetime
import json
import mimetypes
import os
import re
import typing

import aiohttp
import aiohttp.cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import collections.abc
import datetime
import json
import mimetypes
import os
import re
import typing

import aiohttp
import aiohttp.client_exceptions
import duckduckgo_search
import google.oauth2.credentials
import magic
import openai.types.chat
import playwright.async_api
import pydantic
import tiktoken

import bot.slack
import cortex.exceptions
import cortex.llm.openai.agent
import cortex.llm.openai.agent.audio_agent
import cortex.llm.openai.agent.browser_agent
import cortex.llm.openai.agent.grafana_agent
import cortex.llm.openai.agent.image_agent
import cortex.llm.openai.agent.playwright_agent
import cortex.llm.openai.agent.url_open_agent
import cortex.llm.openai.model
import embedding_retrieval.model


class InnerDeepLink(pydantic.BaseModel):
    name: str
    url: str


class DeepLink(pydantic.BaseModel):
    name: str
    url: str
    snippet: str | None = None
    deepLinks: collections.abc.Sequence[InnerDeepLink] | None = None


class License(pydantic.BaseModel):
    name: str
    url: str


class ContractualRule(pydantic.BaseModel):
    _type: str
    targetPropertyName: str
    targetPropertyIndex: int
    mustBeCloseToContent: bool
    license: License
    licenseNotice: str


class ValueItem(pydantic.BaseModel):
    id: str
    name: str
    url: str
    isFamilyFriendly: bool
    displayUrl: str
    snippet: str
    deepLinks: collections.abc.Sequence[DeepLink] | None = None
    dateLastCrawled: str
    language: str
    isNavigational: bool
    contractualRules: collections.abc.Sequence[ContractualRule] | None = None
    thumbnailUrl: str | None = None


class WebPages(pydantic.BaseModel):
    webSearchUrl: str | None = None
    totalEstimatedMatches: int
    value: collections.abc.Sequence[ValueItem]


class SearchResponse(pydantic.BaseModel):
    _type: str
    webPages: WebPages


_BOOSTS = {
    "source": {},
    "source_id": {},
}


def boost(
    result: embedding_retrieval.model.DocumentChunkWithScore,
) -> embedding_retrieval.mo

*[truncated — see source for full prompt]*