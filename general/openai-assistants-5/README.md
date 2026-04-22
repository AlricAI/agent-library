# Openai Assistants

> > The [Assistants API](https://platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAI assistants

> The [Assistants API](https://platform.openai.com/docs/assistants/overview) allows you to build AI assistants within your own applications. An Assistant has instructions and can leverage models, tools, and knowledge to respond to user queries. The Assistants API currently supports three types of tools: Code Interpreter, Retrieval, and Function calling

You can interact with OpenAI Assistants using OpenAI tools or custom tools. When using exclusively OpenAI tools, you can just invoke the assistant directly and get final answers. When using custom tools, you can run the assistant and tool execution loop using the built-in AgentExecutor or easily write your own executor.

Below we show the different ways to interact with Assistants. As a simple example, let's build a math tutor that can write and run code.

### Using only OpenAI tools

```python
from langchain.agents.openai_assistant import OpenAIAssistantRunnable
```

```python
interpreter_assistant = OpenAIAssistantRunnable.create_assistant(
    name="langchain assistant",
    instructions="You are a personal math tutor. Write and run code to answer math questions.",
    tools=[{"type": "code_interpreter"}],
    model="gpt-4-1106-preview",
)
output = interpreter_assistant.invoke({"content": "What's 10 - 4 raised to the 2.7"})
output
```

```output
[ThreadMessage(id='msg_qgxkD5kvkZyl0qOaL4czPFkZ', assistant_id='asst_0T8S7CJuUa4Y4hm1PF6n62v7', content=[MessageContentText(text=Text(annotations=[], value='The result of the calculation \\(10 - 4^{2.7}\\) is approximately \\(-32.224\\).'), type='text')], created_at=1700169519, file_ids=[], metadata={}, object='thread.message', role='assistant', run_id='run_aH3ZgSWNk3vYIBQm3vpE8tr4', thread_id='thread_9K6cYfx1RBh0pOWD8SxwVWW9')]
```

### As a LangChain agent with arbitrary tools

Now let's recreate this functionality using our own tools. For this example we'll use the [E2B sandbox runtime tool](https://e2b.dev/docs?ref=landing-page-get-started).

```py

*[truncated — see source for full prompt]*