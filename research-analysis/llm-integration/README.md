# LLM INTEGRATION

> ## Overview

ambient-fs includes an optional LLM client for haiku-class API calls. This is used for:

1. **File Analysis** (`ambient-fs-analyzer`): Ex

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LLM Integration

## Overview

ambient-fs includes an optional LLM client for haiku-class API calls. This is used for:

1. **File Analysis** (`ambient-fs-analyzer`): Extract imports, exports, and lint hints
2. **Agent Activity Parsing** (`ambient-fs-server`): Enhance non-conforming agent JSONL logs

The LLM is **disabled by default**. When disabled, tier-1 analysis (line counts, TODO counting) still works locally.

## Architecture

```
ambient-fs-server/src/llm.rs (shared LLM client)
           |
           +---> ambient-fs-analyzer (file analysis)
           |      LlmFileAnalyzer uses LlmClient.call_json()
           |
           +---> ambient-fs-server (agent tracker)
                  AgentTracker uses LlmClient.call_json()
```

## API Reference

### LlmConfig

```rust
use ambient_fs_server::LlmConfig;

let config = LlmConfig {
    api_key: std::env::var("ANTHROPIC_API_KEY").ok(),
    model: "claude-haiku-4-5-20251001".to_string(),
    base_url: "https://api.anthropic.com/v1".to_string(),
    max_tokens: 512,
};

// Or use defaults (no API key = disabled)
let config = LlmConfig::default();
```

Fields:
- `api_key: Option<String>` - Anthropic API key (None = disabled)
- `model: String` - Model identifier (default: claude-haiku-4-5-20251001)
- `base_url: String` - API base URL (default: https://api.anthropic.com/v1)
- `max_tokens: usize` - Max tokens in response (default: 512)

### LlmClient

```rust
use ambient_fs_server::{LlmClient, LlmConfig, LlmError};

let client = LlmClient::new(config);

// Check if enabled
if !client.is_enabled() {
    return;
}

// Raw text response
let response: String = client.call(
    "you are a code analyzer",
    "analyze this file"
).await?;

// Structured JSON response
#[derive(Deserialize)]
struct Analysis {
    imports: Vec<String>,
    exports: Vec<String>,
}

let analysis: Analysis = client.call_json(
    "extract imports and exports as JSON",
    code_content
).await?;
```

Methods:
- `new(config: LlmConfig) -> Self`
- `is_e

*[truncated — see source for full prompt]*