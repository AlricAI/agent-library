# Langserve

> [![Release Notes](https://img.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🦜️🏓 LangServe

[![Release Notes](https://img.shields.io/github/release/langchain-ai/langserve)](https://github.com/langchain-ai/langserve/releases)
[![Downloads](https://static.pepy.tech/badge/langserve/month)](https://pepy.tech/project/langserve)
[![Open Issues](https://img.shields.io/github/issues-raw/langchain-ai/langserve)](https://github.com/langchain-ai/langserve/issues)
[![](https://dcbadge.vercel.app/api/server/6adMQxSpJS?compact=true&style=flat)](https://discord.com/channels/1038097195422978059/1170024642245832774)

🚩 We will be releasing a hosted version of LangServe for one-click deployments of
LangChain applications. [Sign up here](https://airtable.com/apppQ9p5XuujRl3wJ/shrABpHWdxry8Bacm)
to get on the waitlist.

## Overview

[LangServe](https://github.com/langchain-ai/langserve) helps developers
deploy `LangChain` [runnables and chains](https://python.langchain.com/docs/expression_language/)
as a REST API.

This library is integrated with [FastAPI](https://fastapi.tiangolo.com/) and
uses [pydantic](https://docs.pydantic.dev/latest/) for data validation.

In addition, it provides a client that can be used to call into runnables deployed on a
server.
A JavaScript client is available
in [LangChain.js](https://js.langchain.com/docs/ecosystem/langserve).

## Features

- Input and Output schemas automatically inferred from your LangChain object, and
  enforced on every API call, with rich error messages
- API docs page with JSONSchema and Swagger (insert example link)
- Efficient `/invoke`, `/batch` and `/stream` endpoints with support for many
  concurrent requests on a single server
- `/stream_log` endpoint for streaming all (or some) intermediate steps from your
  chain/agent
- **new** as of 0.0.40, supports `/stream_events` to make it easier to stream without needing to parse the output of `/stream_log`.
- Playground page at `/playground/` with streaming output and intermediate steps
- Built-in (optional) tracing to [LangSmith](https://www.langchain.

*[truncated — see source for full prompt]*