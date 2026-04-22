# Gap Analysis

> > **Date**: 2026-03-06
> **AI SDK Version**: `^6.0.111`

## Overview

This document consolidates all identified gaps between our agent SDK wrapper and

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Research: Agent SDK Gap Analysis

> **Date**: 2026-03-06
> **AI SDK Version**: `^6.0.111`

## Overview

This document consolidates all identified gaps between our agent SDK wrapper and the underlying Vercel AI SDK v6 capabilities, specifically for supporting agentic loop control, context management, and sub-agent orchestration.

For detailed analysis of each area, see:

- [prepareStep and activeTools](./prepare-step-and-active-tools.md)
- [experimental_context](./experimental-context.md)
- [Sub-Agent Model](./sub-agent-model.md)

## Gap Summary

| #   | Gap                                    | Severity   | Current State                                                                                            | AI SDK Capability                                                                                        |
| --- | -------------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| 1   | No `prepareStep` support               | **High**   | `AgentConfig`/`AgentOverrides` have no field; `agent.ts` does not pass it to `generateText`/`streamText` | `prepareStep` callback fires before each step; can modify model, messages, tools, system prompt, context |
| 2   | No `activeTools` support               | **High**   | Not exposed at any layer                                                                                 | Top-level and per-step tool restriction via string array of tool names                                   |
| 3   | No `experimental_context` support      | **High**   | Not exposed; `tool()` drops the second execute arg that carries it                                       | User-defined state flows through `prepareStep`, tool `execute`, and lifecycle hooks                      |
| 4   | `tool()` drops AI SDK execute options  | **High**   | `too

*[truncated — see source for full prompt]*