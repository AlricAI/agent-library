# Brave Search

> OpenClaw supports Brave Search API as a `web_search` provider.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Brave Search API

OpenClaw supports Brave Search API as a `web_search` provider.

## Get an API key

1. Create a Brave Search API account at [https://brave.com/search/api/](https://brave.com/search/api/)
2. In the dashboard, choose the **Search** plan and generate an API key.
3. Store the key in config or set `BRAVE_API_KEY` in the Gateway environment.

## Config example

```json5
{
  plugins: {
    entries: {
      brave: {
        config: {
          webSearch: {
            apiKey: "BRAVE_API_KEY_HERE",
            mode: "web", // or "llm-context"
          },
        },
      },
    },
  },
  tools: {
    web: {
      search: {
        provider: "brave",
        maxResults: 5,
        timeoutSeconds: 30,
      },
    },
  },
}
```

Provider-specific Brave search settings now live under `plugins.entries.brave.config.webSearch.*`.
Legacy `tools.web.search.apiKey` still loads through the compatibility shim, but it is no longer the canonical config path.

`webSearch.mode` controls the Brave transport:

- `web` (default): normal Brave web search with titles, URLs, and snippets
- `llm-context`: Brave LLM Context API with pre-extracted text chunks and sources for grounding

## Tool parameters

| Parameter     | Description                                                         |
| ------------- | ------------------------------------------------------------------- |
| `query`       | Search query (required)                                             |
| `count`       | Number of results to return (1-10, default: 5)                      |
| `country`     | 2-letter ISO country code (e.g., "US", "DE")                        |
| `language`    | ISO 639-1 language code for search results (e.g., "en", "de", "fr") |
| `search_lang` | Brave search-language code (e.g., `en`, `en-gb`, `zh-hans`)         |
| `ui_lang`     | ISO language code for UI elements                                   |
| `freshness`   | Time filter: `day` (24h), `week`, `month`, or `year`              

*[truncated — see source for full prompt]*