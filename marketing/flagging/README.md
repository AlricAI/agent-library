# Flagging

> ## Overview

The Genonaut Content Flagging System automatically detects and flags content containing potentially problematic words. It provides an adm

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Content Flagging System Documentation

## Overview

The Genonaut Content Flagging System automatically detects and flags content containing potentially problematic words. It provides an administrative interface for reviewing and managing flagged content with comprehensive risk metrics.

## Features

- **Automatic Detection**: Content is automatically scanned for problematic words during creation
- **Risk Scoring**: Sophisticated risk calculation based on word count, percentage, and diversity
- **Admin Management**: Full CRUD interface for reviewing, filtering, and managing flagged content
- **Manual Scanning**: Ability to manually scan existing content
- **Bulk Operations**: Delete multiple flagged items at once
- **Statistics**: Real-time statistics about flagged content
- **Flexible Configuration**: Configurable danger word list via text file

## Documentation overview

- **Quick Start**: [5-Minute Setup Guide](docs/flagging-quickstart.md) - Get started fast!
- **Full Guide**: [Content Flagging Documentation](docs/flagging.md) - Complete API reference and examples
- **Testing**: [Testing Guide](docs/flagging-testing.md) - Test suites and manual testing checklist
- **API Reference**: See `/api/v1/admin/flagged-content` endpoints in API docs (http://localhost:8001/docs)
- **Implementation Spec**: [Technical Details](notes/issues/by_priority/low/flagging.md) - Phase-by-phase implementation notes

## Quick Setup

1. Create your flag words configuration:
   ```bash
   cp docs/flag-words.txt.example flag-words.txt
   ```

2. Edit `flag-words.txt` to add words that should trigger flagging

3. Content is automatically flagged during creation - no additional setup needed!

## Configuration

### Flag Words File

Create a `flag-words.txt` file in the project root directory:

```bash
cp docs/flag-words.txt.example flag-words.txt
```

Edit the file to add words that should trigger flagging:

```
# Comment lines start with #
violence
weapon
hatred
explicit
# Add more words as

*[truncated — see source for full prompt]*