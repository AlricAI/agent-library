# Ui

> You can use a prebuilt chat UI for interacting with any LangGraph agent through the [Agent Chat UI](https://github.

## Model
- **Default:** `claude-sonnet-4-5`

## Tags
`agent`

## System Prompt
# UI

You can use a prebuilt chat UI for interacting with any LangGraph agent through the [Agent Chat UI](https://github.com/langchain-ai/agent-chat-ui). Using the [deployed version](https://agentchat.vercel.app) is the quickest way to get started, and allows you to interact with both local and deployed graphs.

## Run agent in UI

First, set up LangGraph API server [locally](../tutorials/langgraph-platform/local-server.md) or deploy your agent on [LangGraph Platform](https://langchain-ai.github.io/langgraph/cloud/quick_start/).

Then, navigate to [Agent Chat UI](https://agentchat.vercel.app), or clone the repository and [run the dev server locally](https://github.com/langchain-ai/agent-chat-ui?tab=readme-ov-file#setup):

<video controls src="../assets/base-chat-ui.mp4" type="video/mp4"></video>

!!! Tip

    UI has out-of-box support for rendering tool calls, and tool result messages. To customize what messages are shown, see the [Hiding Messages in the Chat](https://github.com/langchain-ai/agent-chat-ui?tab=readme-ov-file#hiding-messages-in-the-chat) section in the Agent Chat UI documentation.

## Add human-in-the-loop

Agent Chat UI has full support for [human-in-the-loop](../concepts/human_in_the_loop.md) workflows. To try it out, replace the agent code in `src/agent/graph.py` (from the [deployment](../tutorials/langgraph-platform/local-server.md) guide) with this [agent implementation](../how-tos/human_in_the_loop/add-human-in-the-loop.md#add-interrupts-to-any-tool):

<video controls src="../assets/interrupt-chat-ui.mp4" type="video/mp4"></video>

!!! Important

    Agent Chat UI works best if your LangGraph agent interrupts using the @[`HumanInterrupt` schema][HumanInterrupt]. If you do not use that schema, the Agent Chat UI will be able to render the input passed to the `interrupt` function, but it will not have full support for resuming your graph.

## Generative UI

You can also use generative UI in the Agent Chat UI.

Generative UI allows you to define [Re

*[truncated — see source for full prompt]*