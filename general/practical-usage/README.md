# PRACTICAL USAGE

> Real-world examples of using CloudCurio agents, tools, and skills.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CloudCurio Practical Usage Guide

Real-world examples of using CloudCurio agents, tools, and skills.

## Installation

```bash
# 1. Bootstrap
cd /path/to/cloudcurio-monorepo
./scripts/bootstrap.sh

# 2. Install integrations
./scripts/install_integrations.sh all

# 3. Activate environment
source activate_cloudcurio.sh
```

## Using Tools Directly

### LLM Completions

```python
from agents.tools.llm_tools import llm_completion_tool

llm = llm_completion_tool({
    "provider": "ollama",
    "model": "qwen2.5-coder",
    "temperature": 0.7
})

result = llm.execute(prompt="Explain Python decorators")
print(result["text"])
```

### Web Research

```python
from agents.tools.web_tools import search_engine_tool, web_scraper_tool

# Search
search = search_engine_tool()
results = search.execute(query="Python async programming", num_results=5)

# Scrape
scraper = web_scraper_tool()
content = scraper.execute(url="https://example.com", selector="article")
print(content["content"])
```

### File Operations

```python
from agents.tools.file_tools import file_reader_tool, file_writer_tool

# Read
reader = file_reader_tool()
data = reader.execute(filepath="data.txt")

# Write
writer = file_writer_tool({"base_path": "output"})
writer.execute(filepath="result.txt", content="Hello World")
```

### Data Processing

```python
from agents.tools.data_tools import data_transform_tool

transformer = data_transform_tool()

data = [
    {"name": "Alice", "score": 95, "grade": "A"},
    {"name": "Bob", "score": 87, "grade": "B"},
    {"name": "Charlie", "score": 92, "grade": "A"}
]

# Filter
filtered = transformer.execute(
    data=data,
    operation="filter",
    condition={"grade": "A"}
)
print(filtered["result"])

# Aggregate
avg = transformer.execute(
    data=data,
    operation="aggregate",
    field="score",
    function="avg"
)
print(f"Average score: {avg['result']}")
```

### System Monitoring

```python
from agents.tools.system_tools import system_info_tool, health_check_tool

# Sy

*[truncated — see source for full prompt]*