# Root Agent

> import collections.abc
import os
import re
import typing

import google.oauth2.credentials
import openai.types.chat
import playwright.async_api
import

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import collections.abc
import os
import re
import typing

import google.oauth2.credentials
import openai.types.chat
import playwright.async_api
import pydantic
import tiktoken

import cortex.exceptions
import cortex.llm.openai.agent
import cortex.llm.openai.agent.browser_agent
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
) -> embedding_retrieval.model.DocumentChunkWithScore:
    for pattern, source_boost in _BOOSTS["source"].items():
        if isinstance(pattern, str) and pattern == result.metadata.source:
            result.score *= source_boost

        if isinstance(pattern, re.Pattern) and pattern.match(result.metadata.source):
            result.score *= source_boost

    for p

*[truncated — see source for full prompt]*