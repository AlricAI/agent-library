# Grafana Agent

> import contextlib
import typing

import mcp.client.sse
import mcp.shared.exceptions
import tiktoken

import cortex.llm.openai.model


def _with_defaul

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import contextlib
import typing

import mcp.client.sse
import mcp.shared.exceptions
import tiktoken

import cortex.llm.openai.model


def _with_default_datasource(
    func: typing.Callable[
        ..., typing.Awaitable[cortex.llm.openai.agent.FunctionResult]
    ],
    datasource: str,
) -> typing.Callable[..., typing.Awaitable[cortex.llm.openai.agent.FunctionResult]]:
    async def wrapper(
        context: cortex.llm.openai.agent.Context, **arguments
    ) -> cortex.llm.openai.agent.FunctionResult:
        arguments["datasourceUid"] = datasource
        return await func(context, **arguments)

    return wrapper


class GrafanaAgent(cortex.llm.openai.agent.Agent):
    url: str

    def __init__(
        self,
        model: cortex.llm.openai.model.CompletionModel,
        encoder: tiktoken.Encoding,
        url: str,
    ):
        self.model = model
        self.encoder = encoder
        self.url = url
        self.functions = {}

    async def __aenter__(self):
        self._stack = contextlib.AsyncExitStack()

        read, write = await self._stack.enter_async_context(
            mcp.client.sse.sse_client(self.url)
        )
        self._session = await self._stack.enter_async_context(
            mcp.ClientSession(read, write)
        )

        await self._session.initialize()

        response = await self._session.list_tools()
        for tool in response.tools:
            if tool.name in ["list_contact_points"]:
                continue

            async def _func(
                context: cortex.llm.openai.agent.Context,
                *,
                _session=self._session,
                _tool_name=tool.name,
                **arguments,
            ) -> cortex.llm.openai.agent.FunctionResult:
                try:
                    result = await _session.call_tool(_tool_name, arguments=arguments)
                    return cortex.llm.openai.agent.FunctionResult(
                        response="\n".join(
                            [
   

*[truncated — see source for full prompt]*