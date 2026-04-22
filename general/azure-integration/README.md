# AZURE INTEGRATION

> This guide covers Azure OpenAI configuration for Amplihack.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure OpenAI Integration Guide

This guide covers Azure OpenAI configuration for Amplihack.

## Configuration Reference

### Required Variables

```env
# Your Azure OpenAI API key
OPENAI_API_KEY="your-azure-openai-api-key-here"  # pragma: allowlist secret

# Azure OpenAI endpoint URL with deployment and API version
OPENAI_BASE_URL="https://your-resource.openai.azure.com/openai/deployments/gpt-4/chat/completions?api-version=2025-01-01-preview"

# Azure-specific settings
AZURE_OPENAI_KEY="your-azure-openai-api-key-here"
AZURE_API_VERSION="2025-01-01-preview"
```

## Azure Endpoint URL Format

Your `OPENAI_BASE_URL` should follow this pattern:

```
https://<resource-name>.openai.azure.com/openai/deployments/<deployment-name>/chat/completions?api-version=<version>
```

**Examples:**

```env
# GPT-4 deployment
OPENAI_BASE_URL="https://mycompany-ai.openai.azure.com/openai/deployments/gpt-4/chat/completions?api-version=2025-01-01-preview"

# GPT-4o deployment
OPENAI_BASE_URL="https://eastus-openai.openai.azure.com/openai/deployments/gpt-4o/chat/completions?api-version=2025-01-01-preview"

# Custom deployment name
OPENAI_BASE_URL="https://prod-ai.openai.azure.com/openai/deployments/my-gpt4-model/chat/completions?api-version=2025-01-01-preview"

# Azure Responses API (for structured output)
OPENAI_BASE_URL="https://mycompany-ai.openai.azure.com/openai/responses?api-version=2025-04-01-preview"
```

## Troubleshooting

### Authentication Errors

**Error:** `401 Unauthorized` or `403 Forbidden`

**Solutions:**

1. **Verify API key**: Test with `curl` directly to Azure endpoint
2. **Check permissions**: Ensure key has access to the deployment
3. **Validate endpoint**: Confirm deployment name and resource name

### Connection Timeouts

**Error:** `Request timed out` or slow responses

**Solutions:**

1. **Check region**: Use Azure region closest to your location
2. **Verify endpoint**: Ensure the endpoint URL is correct

### Model Not Found

**Error:** `The model 'gpt-4' does n

*[truncated — see source for full prompt]*