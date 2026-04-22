# Frontmatter And Env

> ## 🎯 Overview

📋 Shared infrastructure modules used across all automation tasks.
🧩 Provides YAML frontmatter parsing, environment configuration, HT

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔧 Infrastructure — Frontmatter, Environment, HTML, Timer, and Pipeline

## 🎯 Overview

📋 Shared infrastructure modules used across all automation tasks.
🧩 Provides YAML frontmatter parsing, environment configuration, HTML utilities, timing, and pipeline orchestration.

## 📦 Components

### 📄 Frontmatter (`haskell/src/Automation/Frontmatter.hs`)

- 🔍 parseFrontmatter extracts YAML key-value pairs from markdown content between triple-dash delimiters
- 📖 readReflection reads a daily reflection file and detects social media section presence
- 📝 readNote reads an arbitrary note file
- 🗺️ getReflectionPath constructs the file path for a dated reflection
- 🔧 Simple text-based parsing without external YAML library dependency

### 🏗️ YAML Value Types (YamlValue)

- 📐 YamlValue is a sum type with two constructors: YamlText for double-quoted strings and YamlBool for native YAML booleans
- 🔐 renderYamlValue serializes values according to the YAML 1.2 specification: strings are always double-quoted with proper escaping, booleans render as unquoted true or false
- 🧩 Single source of truth: all modules import YamlValue and renderYamlValue from Automation.Frontmatter
- ⚠️ Never construct YAML key-value lines without rendering values through renderYamlValue or quoteYamlValue

### 🧹 YAML Sanitization (sanitizeForYaml)

- 🧼 Pre-processes AI-generated text before YAML serialization
- 📝 Replaces newlines, carriage returns, and tabs with spaces
- 🗑️ Removes double quotes, single quotes, backslashes, and backticks
- 📏 Collapses multiple spaces and trims whitespace
- 🔧 Applied to image prompts and other AI-generated content before quoting

### 🌍 Environment (`haskell/src/Automation/Env.hs`)

- ✅ validateEnvironment validates and constructs configuration from environment variables
- 🚫 isPlatformDisabled checks if a platform is disabled via env var (true, 1, yes)
- 📅 getYesterdayDate returns yesterday's date in YYYY-MM-DD format
- 🔑 Requires GEMINI_API_KEY, OBSIDIA

*[truncated — see source for full prompt]*