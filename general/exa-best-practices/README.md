# Exa Best Practices

> > ## Documentation Index
> Fetch the complete documentation index at: https://exa.ai/docs/llms.txt
> Use this file to discover all available pages bef

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
> ## Documentation Index
> Fetch the complete documentation index at: https://exa.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Search Best Practices

> Best practices for using Exa's Search API

Exa's Search API returns a list of webpages and their contents based on a natural language search query. Results are optimized for LLM consumption, enabling higher-quality completions with clean, token efficent data.

## Key Benefits

* **Token efficient**: Use `highlights` to get key excerpts relevant to your query, reducing token usage by 10x compared to full text, without adding latency.
* **Specialized index coverage**: State of the art search performance on [people](https://exa.ai/blog/people-search-benchmark), [company](https://exa.ai/blog/company-search-benchmarks), and code using Exa's in-house search indexes.
* **Incredible speed**: Providing the fastest search available without compromising on quality, allowing for search to be added to real-time workflows.

## Request Fields

The `query` parameter is required for all search requests. The remaining fields are optional. See the [API Reference](/reference/search) for complete parameter details.

| Field              | Type      | Notes                                                                                                                                   | Example                                        |
| ------------------ | --------- | --------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| query              | string    | The search query. Supports long, semantically rich descriptions for finding niche content.                                              | "blog post about embeddings and vector search" |
| type               | string    | Search method: `auto` (highest quality search), `fast` (high quality and lower latency)

*[truncated — see source for full prompt]*