# Quick Start

> To best understand the agent framework, let's build an agent that has two tools: one to look things up online, and one to look up specific data that we've loaded into a index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quickstart

To best understand the agent framework, let's build an agent that has two tools: one to look things up online, and one to look up specific data that we've loaded into a index.

This will assume knowledge of [LLMs](/docs/modules/model_io/) and [retrieval](/docs/modules/data_connection/) so if you haven't already explored those sections, it is recommended you do so.

## Setup: LangSmith

By definition, agents take a self-determined, input-dependent sequence of steps before returning a user-facing output. This makes debugging these systems particularly tricky, and observability particularly important. [LangSmith](/docs/langsmith) is especially useful for such cases.

When building with LangChain, all steps will automatically be traced in LangSmith.
To set up LangSmith we just need set the following environment variables:

```bash
export LANGCHAIN_TRACING_V2="true"
export LANGCHAIN_API_KEY="<your-api-key>"
```

## Define tools

We first need to create the tools we want to use. We will use two tools: [Tavily](/docs/integrations/tools/tavily_search) (to search online) and then a retriever over a local index we will create

### [Tavily](/docs/integrations/tools/tavily_search)

We have a built-in tool in LangChain to easily use Tavily search engine as tool.
Note that this requires an API key - they have a free tier, but if you don't have one or don't want to create one, you can always ignore this step.

Once you create your API key, you will need to export that as:

```bash
export TAVILY_API_KEY="..."
```

```python
from langchain_community.tools.tavily_search import TavilySearchResults
```

```python
search = TavilySearchResults()
```

```python
search.invoke("what is the weather in SF")
```

```output
[{'url': 'https://www.weatherapi.com/',
  'content': "{'location': {'name': 'San Francisco', 'region': 'California', 'country': 'United States of America', 'lat': 37.78, 'lon': -122.42, 'tz_id': 'America/Los_Angeles', 'localtime_epoch': 1712847697, 'localtime':

*[truncated — see source for full prompt]*