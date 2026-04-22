# CLI GUIDE

> Command-line interface for Azure HayMaker

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker CLI Guide
{: .no_toc }

Complete guide for using the Azure HayMaker command-line interface.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Installation

### From PyPI (Recommended)

```bash
pip install haymaker-cli
```

### From Source

```bash
cd cli
pip install -e .
```

See the [CLI source code](https://github.com/rysweet/AzureHayMaker/tree/main/cli/src/haymaker_cli) for implementation details.

### Development Installation

```bash
cd cli
pip install -e ".[dev]"
```

See [pyproject.toml](https://github.com/rysweet/AzureHayMaker/blob/main/cli/pyproject.toml) for development dependencies.

## Configuration

The CLI can be configured using:
1. Configuration file (`~/.haymaker/config.yaml`)
2. Environment variables
3. Command-line options

### Priority Order

1. Command-line options (highest priority)
2. Environment variables
3. Configuration file
4. Default values (lowest priority)

### Configuration File

Create `~/.haymaker/config.yaml`:

```yaml
profiles:
  default:
    endpoint: https://haymaker-dev.azurewebsites.net
    auth:
      type: api_key
      api_key: your-api-key-here

  production:
    endpoint: https://haymaker-prod.azurewebsites.net
    auth:
      type: azure_ad
      tenant_id: your-tenant-id

default_profile: default
```

### Environment Variables

```bash
export HAYMAKER_ENDPOINT=https://haymaker-dev.azurewebsites.net
export HAYMAKER_API_KEY=your-api-key
export HAYMAKER_PROFILE=default

# Optional: Configure Anthropic model for AI email generation
export ANTHROPIC_MODEL=claude-sonnet-4-5-20250929
```

See [Configure Anthropic Model](/AzureHayMaker/howto/configure-anthropic-model) for details on model selection and configuration.

### Using the Config Command

```bash
# Set configuration values
haymaker config set endpoint https://haymaker-dev.azurewebsites.net
haymaker config set api-key your-api-key

# Get configuration values
haymaker config get endpoint

# List all configuration
ha

*[truncated — see source for full prompt]*