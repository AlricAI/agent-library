# Multi Agent Orchestration

> Patterns for coordinating multiple agents: sequential chains, parallel execution, agent handoff, voting, and hierarchical delegation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Orchestrate Multiple Agents

Patterns for coordinating multiple agents: sequential chains, parallel execution, agent handoff, voting, and hierarchical delegation.

## Prerequisites

- `@funkai/agents` installed
- Familiarity with `agent()`, `flowAgent()`, `$.agent`, `$.map`, `$.all`, and `$.race`
- Understanding of subagents (the `agents` field on `AgentConfig`)

## Steps

### 1. Chain agents sequentially

Pass the output of one agent as input to the next using `$.agent` steps in sequence.

```ts
import { flowAgent, agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";
import { z } from "zod";

const researcher = agent({
  name: "researcher",
  model: openai("gpt-4.1"),
  input: z.object({ topic: z.string() }),
  prompt: ({ input }) => `Research the topic thoroughly:\n\n${input.topic}`,
});

const writer = agent({
  name: "writer",
  model: openai("gpt-4.1"),
  input: z.object({ research: z.string(), topic: z.string() }),
  prompt: ({ input }) =>
    `Write an article about "${input.topic}" using this research:\n\n${input.research}`,
});

const editor = agent({
  name: "editor",
  model: openai("gpt-4.1"),
  input: z.object({ draft: z.string() }),
  prompt: ({ input }) => `Edit this article for clarity and correctness:\n\n${input.draft}`,
});

const pipeline = flowAgent(
  {
    name: "content-pipeline",
    input: z.object({ topic: z.string() }),
    output: z.object({ article: z.string() }),
  },
  async ({ input, $ }) => {
    const research = await $.agent({
      id: "research",
      agent: researcher,
      input: { topic: input.topic },
    });
    if (!research.ok) return { article: "Research failed" };

    const draft = await $.agent({
      id: "write",
      agent: writer,
      input: { research: research.output, topic: input.topic },
    });
    if (!draft.ok) return { article: "Writing failed" };

    const edited = await $.agent({
      id: "edit",
      agent: editor,
      input: { draft: draft.output },
    });

    return { a

*[truncated — see source for full prompt]*