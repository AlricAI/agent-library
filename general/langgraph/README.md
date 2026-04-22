# Langgraph

> [![Downloads](https://static.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🦜🕸️LangGraph

[![Downloads](https://static.pepy.tech/badge/langgraph/month)](https://pepy.tech/project/langgraph)
[![Open Issues](https://img.shields.io/github/issues-raw/langchain-ai/langgraph)](https://github.com/langchain-ai/langgraph/issues)
[![](https://dcbadge.vercel.app/api/server/6adMQxSpJS?compact=true&style=flat)](https://discord.com/channels/1038097195422978059/1170024642245832774)
[![Docs](https://img.shields.io/badge/docs-latest-blue)](https://langchain-ai.github.io/langgraph/)

⚡ Building language agents as graphs ⚡

## Overview

[LangGraph](https://langchain-ai.github.io/langgraph/) is a library for building stateful, multi-actor applications with LLMs.
Inspired by [Pregel](https://research.google/pubs/pub37252/) and [Apache Beam](https://beam.apache.org/), LangGraph lets you coordinate and checkpoint multiple chains (or actors) across cyclic computational steps using regular python functions (or [JS](https://github.com/langchain-ai/langgraphjs)). The public interface draws inspiration from [NetworkX](https://networkx.org/documentation/latest/).

The main use is for adding **cycles** and **persistence** to your LLM application. If you only need quick Directed Acyclic Graphs (DAGs), you can already accomplish this using [LangChain Expression Language](https://python.langchain.com/docs/expression_language/).

Cycles are important for agentic behaviors, where you call an LLM in a loop, asking it what action to take next.

## Installation

```shell
pip install -U langgraph
```

## Quick start

One of the central concepts of LangGraph is state. Each graph execution creates a state that is passed between nodes in the graph as they execute, and each node updates this internal state with its return value after it executes. The way that the graph updates its internal state is defined by either the type of graph chosen or a custom function.

State in LangGraph can be pretty general, but to keep things simpler to start, we'll show off an example where the gr

*[truncated — see source for full prompt]*