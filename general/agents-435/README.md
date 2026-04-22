# Agents

> This guide shows you how to create custom agents in Mastra using the patterns established in this template.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Creating Custom Agents

This guide shows you how to create custom agents in Mastra using the patterns established in this template.

## Agent Basics

An agent in Mastra is defined using Zod-validated configuration:

```typescript
import { Agent } from "@mastra/core/agent";
import { openai } from "@ai-sdk/openai";
import { z } from "zod";

const myAgent = new Agent({
  id: "my-agent",                    // Unique identifier
  name: "My Agent",                  // Display name
  instructions: "You are...",        // System prompt
  model: openai("gpt-4o-mini"),     // LLM model
  tools: { /* optional tools */ },   // Available tools
  memory: myMemory,                  // Optional memory
});
```

## Step-by-Step: Create a Code Review Agent

### 1. Define the Agent File

Create `src/agent/src/agents/code-reviewer.ts`:

```typescript
import { Agent } from "@mastra/core/agent";
import { openai } from "@ai-sdk/openai";

/**
 * Code Review Agent - Analyzes code and provides feedback
 */
export const codeReviewerAgent = new Agent({
  id: "code-reviewer",
  name: "Code Reviewer",
  instructions: `You are an expert code reviewer with deep knowledge of:
- TypeScript and JavaScript best practices
- Clean code principles
- Security vulnerabilities
- Performance optimization
- Testing strategies

When reviewing code:
1. Identify potential bugs or issues
2. Suggest improvements
3. Highlight security concerns
4. Recommend best practices
5. Be constructive and specific

Format your response with clear sections for each category.`,
  model: openai("gpt-4o-mini"),
  // We'll add tools in step 3
});
```

### 2. Export the Agent

Update `src/agent/src/agents/index.ts`:

```typescript
export { generalAgent } from "./general.js";
export { weatherAgent } from "./weather.js";
export { routerAgent } from "./router.js";
export { codeReviewerAgent } from "./code-reviewer.js"; // Add this
```

### 3. Register with Mastra

Update `src/agent/src/mastra.ts`:

```typescript
import {
  routerAgent

*[truncated — see source for full prompt]*