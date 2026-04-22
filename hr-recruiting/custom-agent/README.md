# Custom Agent

> This notebook goes through how to create your own custom agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Custom agent

This notebook goes through how to create your own custom agent.

In this example, we will use OpenAI Tool Calling to create this agent.
**This is generally the most reliable way to create agents.**

We will first create it WITHOUT memory, but we will then show how to add memory in.
Memory is needed to enable conversation.

## Load the LLM

First, let's load the language model we're going to use to control the agent.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo", temperature=0)
```

## Define Tools

Next, let's define some tools to use.
Let's write a really simple Python function to calculate the length of a word that is passed in.

Note that here the function docstring that we use is pretty important. Read more about why this is the case [here](/docs/modules/tools/custom_tools)

```python
from langchain.agents import tool


@tool
def get_word_length(word: str) -> int:
    """Returns the length of a word."""
    return len(word)


get_word_length.invoke("abc")
```

```output
3
```

```python
tools = [get_word_length]
```

## Create Prompt

Now let us create the prompt.
Because OpenAI Function Calling is finetuned for tool usage, we hardly need any instructions on how to reason, or how to output format.
We will just have two input variables: `input` and `agent_scratchpad`. `input` should be a string containing the user objective. `agent_scratchpad` should be a sequence of messages that contains the previous agent tool invocations and the corresponding tool outputs.

```python
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are very powerful assistant, but don't know current events",
        ),
        ("user", "{input}"),
        MessagesPlaceholder(variable_name="agent_scratchpad"),
    ]
)
```

## Bind tools to LLM

How does the agent know what tools it can use?

In this case we're 

*[truncated — see source for full prompt]*