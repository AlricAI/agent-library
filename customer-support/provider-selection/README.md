# Provider Selection

> CycoD supports multiple AI providers including OpenAI, Azure OpenAI, GitHub Copilot, and Anthropic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Provider Selection

CycoD supports multiple AI providers including OpenAI, Azure OpenAI, GitHub Copilot, and Anthropic. This document explains how to select and configure different providers.

## Supported Providers

CycoD currently supports the following AI providers:

| Provider | Required Credentials | Features |
|----------|---------------------|----------|
| GitHub Copilot | `GITHUB_TOKEN` | GitHub Copilot models |
| Anthropic | `ANTHROPIC_API_KEY` | Anthropic Claude models |
| OpenAI | `OPENAI_API_KEY` | Standard OpenAI API |
| Azure OpenAI | `AZURE_OPENAI_API_KEY` | OpenAI models hosted on Azure |

## Default Provider Selection

By default, CycoD selects a provider by checking for the necessary environment variables in the following order:

1. GitHub Copilot (if `GITHUB_TOKEN` is set)
2. Anthropic (if `ANTHROPIC_API_KEY` is set)
3. OpenAI (if `OPENAI_API_KEY` is set)
4. Azure OpenAI (if `AZURE_OPENAI_API_KEY` is set)

This means that if you have multiple sets of credentials in your environment, CycoD will use the first one it finds according to this priority order.

## Ways to Select a Provider

There are several methods to explicitly select a provider, overriding the default behavior:

### 1. Command-Line Provider Flags

Use these command-line flags to explicitly select a provider:

```bash
cycod --use-openai        # Use OpenAI API
cycod --use-azure-openai  # Use Azure OpenAI API
cycod --use-copilot       # Use GitHub Copilot
cycod --use-anthropic     # Use Anthropic API
```

These flags override the default provider selection order. All necessary credentials must still be available in your environment or configuration files.

### 2. Configuration File Setting

Set your preferred provider in any configuration file (global, user, or local):

```yaml
app:
  preferredProvider: "openai"  # Can be "openai", "azure-openai", "copilot", "anthropic"
```

Or using the config command:

```bash
cycod config set app.preferredProvider openai
```

### 3. Environment Var

*[truncated — see source for full prompt]*