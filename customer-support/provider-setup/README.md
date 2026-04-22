# Provider Setup

> The pipeline supports multiple LLM providers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LLM Provider Setup

The pipeline supports multiple LLM providers. In product mode, the packaged
app, web app, CLI, and TUI all resolve provider settings from the same shared
settings backend in `scripts/settings_store.py`.

Under the hood, those values live in the runtime app-home env files returned by
`scripts/app_paths.py`. They are local runtime state, not committed repo
configuration.

## Supported Providers

| Provider | CLI Binary | Default Model | Install |
|----------|-----------|---------------|---------|
| `claude` | `claude` | `claude-sonnet-4-6` | [claude.ai/download](https://claude.ai/download) |
| `codex` | `codex` | `gpt-5.4` | `brew install codex` or `npm install -g @openai/codex` |
| `openai` (default) | `python openai_provider.py` | `gpt-5.4` | `uv add openai` + API key |
| `gemini` | `gemini` | `gemini-3-flash-preview` | [ai.google.dev/gemini-api/docs/quickstart](https://ai.google.dev/gemini-api/docs/quickstart) |
| `gemini-flash` | `gemini` | `gemini-3-flash-preview` | Same as gemini |

## Quick Start: Switch to Codex (GPT)

1. **Install:** `brew install codex`
2. **Authenticate** (pick one):
   - **OAuth:** `codex login` (opens browser)
   - **API key:** `job-assets settings set --codex-api-key sk-proj-...`
3. **Set the shared default provider:**
   ```bash
   job-assets settings set --default-provider codex
   ```
4. Run the pipeline as normal. All surfaces now resolve Codex from the same
   runtime settings.

## Quick Start: OpenAI API

1. **Get an API key** from [platform.openai.com](https://platform.openai.com)
2. **Configure the shared settings backend:**
   ```bash
   job-assets settings set --default-provider openai --openai-api-key sk-proj-...
   ```
3. Run the pipeline as normal. All surfaces now use OpenAI's Responses API
   directly.

### OpenAI Key Pool

If you want to spread OpenAI traffic across multiple keys, configure them in
the shared settings backend as a comma-separated pool:

```bash
job-assets settings set \
  --default-p

*[truncated — see source for full prompt]*