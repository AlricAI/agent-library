# Scripts Directory Architecture Guide

> description: globs: alwaysApply: false

## Tags
`typescript` `openai`

## System Prompt
---
description:
globs:
alwaysApply: false
---
# Scripts Directory Architecture Guide

This project uses a modular scripts directory structure for maintainability and clear separation of concerns.

## 📁 Directory Structure

### Core Module (`scripts/core/`)
- **[scripts/core/constants.ts](mdc:scripts/core/constants.ts)** - Central configuration, paths, and constants
- **[scripts/core/model.ts](mdc:scripts/core/model.ts)** - OpenAI model configuration and API calls

### Utility Modules (`scripts/utils/`)
- **[scripts/utils/file.ts](mdc:scripts/utils/file.ts)** - File operations (read, write, directory management)
- **[scripts/utils/common.ts](mdc:scripts/utils/common.ts)** - General utility functions (string processing, arrays)
- **[scripts/utils/logger.ts](mdc:scripts/utils/logger.ts)** - Custom logging system with structured output

### Processing Modules
- **[scripts/parsers/agent-parser.ts](mdc:scripts/parsers/agent-parser.ts)** - Parse Agent configuration files
- **[scripts/processors/category-processor.ts](mdc:scripts/processors/category-processor.ts)** - AI-powered category assignment
- **[scripts/processors/i18n-processor.ts](mdc:scripts/processors/i18n-processor.ts)** - Translation and internationalization

### Validation Modules
- **[scripts/validators/agent-validator.ts](mdc:scripts/validators/agent-validator.ts)** - Schema validation and formatting
- **[scripts/validators/language-validator.ts](mdc:scripts/validators/language-validator.ts)** - Language detection and validation using @yutengjing/eld

### Build System
- **[scripts/builders/agent-builder.ts](mdc:scripts/builders/agent-builder.ts)** - Build all language versions of Agent files
- **[scripts/formatters/agent-formatter.ts](mdc:scripts/formatters/agent-formatter.ts)** - Format and process Agent configurations

### Command Line Tools (`scripts/commands/`)
- **[scripts/commands/build.ts](mdc:scripts/commands/build.ts)** - Main build command
- **[scripts/commands/format.ts](mdc:scripts/commands/for

*[truncated — see source for full prompt]*