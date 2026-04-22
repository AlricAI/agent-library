# DEVELOPMENT GUIDELINES

> ## Configuration Management

### The .env Rule: NO HARDCODED VALUES

**RULE**: All user-configurable values MUST be in `.env` with environment variabl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Development Guidelines

## Configuration Management

### The .env Rule: NO HARDCODED VALUES

**RULE**: All user-configurable values MUST be in `.env` with environment variable support.

**✅ GOOD**:
```python
import os
from helpers.config import load_config

# Use config system
config = load_config()
api_key = config.get('API_KEY')

# Or direct environment access with defaults
timeout = int(os.environ.get('PROCESSING_TIMEOUT', '30'))
base_url = os.environ.get('API_BASE_URL', 'https://api.example.com')

# Atlas secrets pattern: .env has variable definitions, ~/.secrets/ has values
# .env file contains:
# API_KEY=${API_KEY:-default_value}  # pragma: allowlist secret
# ~/.secrets/atlas.env contains:
# export API_KEY=actual_secret_value  # pragma: allowlist secret
```

**❌ BAD**:
```python
# Never hardcode these values
API_KEY = "sk-1234567890"
TIMEOUT = 30
BASE_URL = "https://api.example.com"
SAVE_FOLDER = "/Users/username/Documents/atlas"
```

### What Must Be Configurable

**Always use .env for**:
- **Credentials**: API keys, passwords, tokens
- **Paths**: File/directory paths, URLs, endpoints
- **Limits**: Timeouts, retry counts, batch sizes
- **Features**: Enable/disable flags, mode switches
- **Services**: Port numbers, host addresses

### Configuration Best Practices

1. **Update env.template**: Add new variables with descriptions
2. **Add to .env**: Use Atlas secrets pattern `VAR=${VAR:-default}`
3. **Add to ~/.secrets/atlas.env**: Set actual secret values with `export VAR=value`
4. **Provide defaults**: Use sensible fallback values
5. **Document requirements**: Mark required vs optional in comments
6. **Type conversion**: Cast strings to appropriate types
7. **Validation**: Check for required variables at startup

### Example Implementation

```python
import os
from typing import Optional

class EmailConfig:
    def __init__(self):
        # Required - will fail if not set
        self.enabled = os.environ.get('GMAIL_ENABLED', 'false').lower() == 'true'


*[truncated — see source for full prompt]*