# Configuration Validation

> Atlas includes a comprehensive configuration validation system that provides detailed error messages and specific guidance for resolving configuration issues.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration Validation System

Atlas includes a comprehensive configuration validation system that provides detailed error messages and specific guidance for resolving configuration issues.

## Features

### ✅ Enhanced Error Messages
- Detailed explanations of what's wrong
- Specific guidance on how to fix issues
- Ready-to-run fix commands
- Links to relevant documentation

### ✅ Multiple Validation Levels
- **Errors**: Issues that prevent Atlas from working
- **Warnings**: Suggestions for better performance, security, or cost optimization
- **Info**: Additional recommendations

### ✅ Smart Detection
- Invalid API key formats
- Placeholder credentials
- Expensive model configurations
- Security and privacy concerns
- Performance optimization opportunities

## Usage

### Command Line Validation

```bash
# Basic validation report
python scripts/validate_config.py

# JSON output for automation
python scripts/validate_config.py --json

# Show only fix commands
python scripts/validate_config.py --fix

# Show only errors (no warnings)
python scripts/validate_config.py --errors-only

# Quiet mode (only output if issues found)
python scripts/validate_config.py --quiet
```

### Programmatic Usage

```python
from helpers.validate import ConfigValidator, validate_config_enhanced

# Load your config
from helpers.config import load_config
config = load_config()

# Enhanced validation with detailed guidance
validator = ConfigValidator()
errors, warnings = validator.validate_config(config)

# Print formatted report
if errors or warnings:
    report = validator.format_validation_report(errors, warnings)
    print(report)

# Or use the convenience function
errors, warnings = validate_config_enhanced(config)
```

## Common Issues and Solutions

### Missing API Keys

**Error**: `OPENROUTER_API_KEY is required when llm_provider is 'openrouter'`

**Solution**:
1. Get your API key from https://openrouter.ai/keys
2. Add it to your `.env` file:
   ```bash
   echo 'OPENROUTER_API_KEY=y

*[truncated — see source for full prompt]*