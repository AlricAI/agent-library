# SCRIPTS README

> ## Overview

This document describes the Python automation scripts for the User Story Workflow System. All scripts follow project coding standards: ty

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Story System - Python Scripts Documentation

## Overview

This document describes the Python automation scripts for the User Story Workflow System. All scripts follow project coding standards: type hints, comprehensive docstrings, error handling, and atomic file operations.

## Installation

```bash
# Install dependencies
pip install -r requirements.txt

# Verify installation
python3 scripts/generate_story_from_yaml.py --help
```

## Scripts

### 1. models.py

**Purpose**: Pydantic models for data validation

**Description**:
- Defines `UserStory`, `Epic`, and all sub-models
- Provides validation for story/epic structures
- Enforces type safety across all scripts
- Validates IDs, priorities, story points, etc.

**Usage**:
```python
from models import UserStory

story = UserStory(**story_data)  # Validates on creation
```

**Line Count**: 255 lines

---

### 2. generate_story_from_yaml.py

**Purpose**: Generate Markdown documentation from YAML story files

**Features**:
- Load YAML story files
- Render Markdown using Jinja2 templates
- Atomic file writes (prevents corruption)
- Single story or batch processing

**Usage**:
```bash
# Generate single story
python3 scripts/generate_story_from_yaml.py --story-id US-0001

# Generate all stories
python3 scripts/generate_story_from_yaml.py --all

# Debug mode
python3 scripts/generate_story_from_yaml.py --all --verbose
```

**Line Count**: 316 lines

---

### 3. validate_story_invest.py

**Purpose**: Validate user stories against INVEST criteria

**INVEST Criteria**:
- **I**ndependent: Minimal blocking dependencies
- **N**egotiable: Flexible, not overly prescriptive
- **V**aluable: Clear business/user value
- **E**stimable: Has story points
- **S**mall: Within sprint capacity (≤8 points)
- **T**estable: Has Given/When/Then acceptance criteria

**Features**:
- Check each INVEST criterion
- Calculate overall score (0-100)
- Provide actionable suggestions
- Save results back to YAML
- JSON or text output

**Usage**:
```ba

*[truncated — see source for full prompt]*