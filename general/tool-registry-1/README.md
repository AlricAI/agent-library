# TOOL REGISTRY

> Comprehensive registry of all available tools in the CloudCurio ecosystem.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tool Registry

Comprehensive registry of all available tools in the CloudCurio ecosystem.

## Categories

### LLM Integration Tools
Located in: `agents/tools/llm_tools.py`

- **llm_completion** - Generate text completions using local or cloud LLMs
  - Supports: Ollama, OpenAI, OpenRouter, Anthropic
  - Use cases: Text generation, code completion, content creation
  
- **llm_embedding** - Generate text embeddings for semantic search
  - Supports: Ollama (nomic-embed-text)
  - Use cases: Similarity search, document indexing, clustering

### Web Interaction Tools
Located in: `agents/tools/web_tools.py`

- **web_scraper** - Extract content and data from web pages
  - Features: CSS selector support, BeautifulSoup parsing
  - Use cases: Data extraction, content monitoring, research

- **api_client** - Make HTTP requests to REST APIs
  - Methods: GET, POST, PUT, DELETE, PATCH
  - Features: Headers, query params, JSON payloads
  - Use cases: API integration, data fetching, webhooks

- **search_engine** - Search the web using DuckDuckGo
  - Features: No API key required, privacy-focused
  - Use cases: Research, fact-checking, discovery

### File System Tools
Located in: `agents/tools/file_tools.py`

- **file_reader** - Read text content from files
  - Features: Encoding support, size limits
  - Use cases: Configuration reading, log analysis, data loading

- **file_writer** - Write text content to files
  - Features: Write/append modes, auto-create directories
  - Use cases: Report generation, logging, data export

- **directory_tool** - List, create, and manage directories
  - Actions: list, create, delete
  - Features: Recursive listing, glob patterns
  - Use cases: File organization, cleanup, discovery

- **file_search** - Search for files by name and content
  - Search types: name pattern, content search
  - Features: Recursive search, pattern matching
  - Use cases: Code search, log analysis, file discovery

### Data Processing Tools
Located in: `agents/tools/data_tool

*[truncated — see source for full prompt]*