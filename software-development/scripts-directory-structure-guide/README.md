# Scripts Directory Structure Guide

> description: globs: alwaysApply: true

## Tags
`typescript` `openai`

## System Prompt
---
description: 
globs: 
alwaysApply: true
---
# Scripts Directory Structure Guide

This project uses an optimized, modular scripts directory structure for better maintainability and clear separation of concerns.

## 📁 Directory Structure Overview

The [scripts/](mdc:scripts) directory is organized into the following modules:

### Core Module (`scripts/core/`)
- **[scripts/core/constants.ts](mdc:scripts/core/constants.ts)** - Central configuration and constants
- **[scripts/core/model.ts](mdc:scripts/core/model.ts)** - OpenAI model configuration

### Utility Modules (`scripts/utils/`)
- **[scripts/utils/file.ts](mdc:scripts/utils/file.ts)** - File operations (read, write, directory management)
- **[scripts/utils/common.ts](mdc:scripts/utils/common.ts)** - General utility functions (string processing, arrays)

### Processing Modules
- **[scripts/parsers/agent-parser.ts](mdc:scripts/parsers/agent-parser.ts)** - Parse Agent configuration files
- **[scripts/processors/category-processor.ts](mdc:scripts/processors/category-processor.ts)** - AI-powered category assignment
- **[scripts/processors/i18n-processor.ts](mdc:scripts/processors/i18n-processor.ts)** - Internationalization and translation
- **[scripts/validators/agent-validator.ts](mdc:scripts/validators/agent-validator.ts)** - Schema validation and formatting

### Build System
- **[scripts/builders/agent-builder.ts](mdc:scripts/builders/agent-builder.ts)** - Build all language versions of Agent files
- **[scripts/formatters/agent-formatter.ts](mdc:scripts/formatters/agent-formatter.ts)** - Format and process Agent configurations

### Command Line Tools (`scripts/commands/`)
- **[scripts/commands/build.ts](mdc:scripts/commands/build.ts)** - Main build command
- **[scripts/commands/format.ts](mdc:scripts/commands/format.ts)** - Format Agent files
- **[scripts/commands/test.ts](mdc:scripts/commands/test.ts)** - Validation tests
- **[scripts/commands/test-locale.ts](mdc:scripts/commands/test-locale.ts)** - Multi-lan

*[truncated — see source for full prompt]*