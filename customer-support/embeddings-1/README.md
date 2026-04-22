# EMBEDDINGS

> floop supports local embedding-based retrieval for semantic behavior matching.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Local Embeddings

floop supports local embedding-based retrieval for semantic behavior matching. This runs a small model on your machine — no API keys or network access required at runtime.

## Overview

When enabled, `floop_active` embeds the current context (file, task, language) and finds the most semantically similar behaviors via vector cosine similarity. This complements the existing predicate matching and spreading activation pipeline by finding relevant behaviors even when their `when` conditions don't exactly match.

## Setup

### Interactive

```bash
floop init
```

The interactive setup prompts whether to download and enable local embeddings (option 4).

### Non-interactive

```bash
# Enable embeddings
floop init --global --embeddings

# Skip embeddings
floop init --global --no-embeddings
```

### What Gets Downloaded

Two runtime dependencies are downloaded to `~/.floop/` (~130 MB total):

| Component | Size | Location |
|-----------|------|----------|
| llama.cpp shared libraries | ~50 MB | `~/.floop/lib/` (`%USERPROFILE%\.floop\lib\` on Windows) |
| nomic-embed-text-v1.5 (Q4_K_M) | ~81 MB | `~/.floop/models/` (`%USERPROFILE%\.floop\models\` on Windows) |

Downloads happen once and are cached. Subsequent `floop init --embeddings` calls detect existing installations and skip re-downloading.

### Auto-detection

After initial setup, the MCP server auto-detects installed dependencies in `~/.floop/` on startup. No explicit configuration is needed — if the libraries and model are present, embeddings are enabled automatically.

## Configuration

### Config file (`~/.floop/config.yaml`)

```yaml
llm:
  provider: local
  enabled: true
  local_lib_path: /home/user/.floop/lib
  local_embedding_model_path: /home/user/.floop/models/nomic-embed-text-v1.5.Q4_K_M.gguf
```

These values are set automatically by `floop init --embeddings`. You can also set them manually:

```bash
floop config set llm.provider local
floop config set llm.local_lib_path ~/.floop/lib
floop

*[truncated — see source for full prompt]*