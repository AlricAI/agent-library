---
name: I18N WORKFLOW
description: > Comprehensive guide to the automated internationalization (i18n) workflow that translates your AI agents into 18 languages using OpenAI GPT models.
model: claude-sonnet-4-5
---
# 🌍 18 Languages - Automated i18n Translation Workflow

> Comprehensive guide to the automated internationalization (i18n) workflow that translates your AI agents into 18 languages using OpenAI GPT models.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Supported Languages](#supported-languages)
- [Prerequisites](#prerequisites)
- [How It Works](#how-it-works)
- [Step-by-Step Workflow](#step-by-step-workflow)
- [File Structure](#file-structure)
- [Configuration](#configuration)
- [Running the Workflow](#running-the-workflow)
- [Understanding the Process](#understanding-the-process)
- [Translation Features](#translation-features)
- [Validation & Quality Control](#validation--quality-control)
- [GitHub Actions Integration](#github-actions-integration)
- [Troubleshooting](#troubleshooting)
- [Advanced Topics](#advanced-topics)

---

## Overview

This project includes an **automated translation workflow** that takes your AI agent definitions from the `/src` directory and automatically:

1. ✅ Formats and validates the agent JSON files
2. ✅ Generates missing content (categories, examples, opening messages)
3. ✅ Translates all text fields to 18 languages using OpenAI GPT
4. ✅ Creates organized translation files in `/locales`
5. ✅ Validates translation quality and language accuracy
6. ✅ Builds a CDN-ready public distribution

**Key Benefit**: Submit your agent in English once, and it becomes available in 18 languages automatically.

---

## Supported Languages

The workflow supports **18 languages** based on BCP 47 standards:

| Code    | Language              | Region        |
| ------- | --------------------- | ------------- |
| `en-US` | English               | United States |
| `ar`    | Arabic                |               |
| `bg-BG` | Bulgarian             | Bulgaria      |
| `zh-CN` | Chinese (Simplified)  | China         |
| `zh-TW` | Chinese (Traditional) | Taiwan        |
| `de-DE` | German                | Germany       |
| `es-ES` | Spanish               | Spain         |
| `fa-IR` | Persian (Farsi)       | Iran          |
| `fr-FR` | French                | France        |
| `it-IT` | Italian               | Italy         |
| `ja-JP` | Japanese              | Japan         |
| `ko-KR` | Korean                | South Korea   |
| `nl-NL` | Dutch                 | Netherlands   |
| `pl-PL` | Polish                | Poland        |
| `pt-BR` | Portuguese            | Brazil        |
| `ru-RU` | Russian               | Russia        |
| `tr-TR` | Turkish               | Turkey        |
| `vi-VN` | Vietnamese            | Vietnam       |

---

## Prerequisites

### Required Environment Variables

You **MUST** have an OpenAI API key configured before running the translation workflow:

#### For Local Development

Create a `.env` file in the project root:

```bash
# .env
OPENAI_API_KEY=sk-your-api-key-here
OPENAI_PROXY_URL=https://api.openai.com/v1 # Optional: custom endpoint
```

#### For GitHub Actions

Add these secrets to your GitHub repository:

1. Go to **Settings** → **Secrets and variables** → **Actions**
2. Add the following secrets:
   - `OPENAI_API_KEY`: Your OpenAI API key
   - `OPENAI_PROXY_URL`: (Optional) Custom OpenAI endpoint
   - `GH_TOKEN`: GitHub token for automated commits

### Required Tools

- **Node.js** 18+ or **Bun** runtime
- **Git** for version control
- OpenAI API account with credits

---

## How It Works

The i18n workflow follows this high-level process:

```
┌─────────────────┐
│  /src/*.json    │  ← Your agent files (English)
│  (41 agents)    │
└────────┬────────┘
         │
         ▼
   bun run format  ← Formats & translates
         │
         ├─ Validates JSON structure
         ├─ Generates missing content
         ├─ Extracts translatable fields
         ├─ Calls OpenAI GPT for translation
         └─ Creates locale files
         │
         ▼
┌─────────────────┐
│ /locales/       │  ← Translation output
│  agent-name/    │
│   ├─ index.json │  (en-US default)
│   ├─ index.ar.json
│   ├─ index.zh-CN.json
│   └─ ... 18 files
└────────┬────────┘
         │
         ▼
   bun run build   ← Builds distribution
         │
         ▼
┌─────────────────┐
│  /public/       │  ← CDN-ready output (generated, gitignored)
│   index.json    │
│   agents/       │
└─────────────────┘
```

> \[!NOTE]: The `/public` directory is in `.gitignore` and only created when you run `bun run build`. It's not committed to Git and not required for the translation workflow.

---

## Step-by-Step Workflow

### Step 1: Create Your Agent

Create a new agent file in `/src`:

```bash
/src/your-agent-name.json
```

Example agent structure:

```json
{
  "author": "your-github-username",
  "config": {
    "systemRole": "You are an expert DeFi analyst specializing in yield optimization..."
  },
  "identifier": "your-agent-name",
  "meta": {
    "title": "Your Agent Title",
    "description": "Brief description of what your agent does",
    "avatar": "🤖",
    "tags": ["defi", "yield", "optimization"]
  },
  "schemaVersion": 1
}
```

### Step 2: Format and Translate

Run the format command:

```bash
bun run format
```

This command will:

- ✅ Validate your JSON structure
- ✅ Generate missing fields (category, examples, opening messages)
- ✅ Extract all translatable content
- ✅ Call OpenAI to translate to 18 languages
- ✅ Create organized folders in `/locales`

**Expected Output:**

```
/locales/
  your-agent-name/
    ├── index.json       (en-US)
    ├── index.ar.json    (Arabic)
    ├── index.bg-BG.json (Bulgarian)
    ├── index.de-DE.json (German)
    ├── index.es-ES.json (Spanish)
    ├── index.fa-IR.json (Persian)
    ├── index.fr-FR.json (French)
    ├── index.it-IT.json (Italian)
    ├── index.ja-JP.json (Japanese)
    ├── index.ko-KR.json (Korean)
    ├── index.nl-NL.json (Dutch)
    ├── index.pl-PL.json (Polish)
    ├── index.pt-BR.json (Portuguese)
    ├── index.ru-RU.json (Russian)
    ├── index.tr-TR.json (Turkish)
    ├── index.vi-VN.json (Vietnamese)
    ├── index.zh-CN.json (Simplified Chinese)
    └── index.zh-TW.json (Traditional Chinese)
```

### Step 3: Validate Translations (Optional)

Validate the quality of translations:

```bash
# Validate all translation files
bun run i18n:validate

# Validate and fix issues
bun run i18n:fix

# Validate and delete invalid files
bun run i18n:clean
```

### Step 4: Build for Distribution (Optional)

Build the final public distribution:

```bash
bun run build
```

This creates CDN-ready files in `/public` (gitignored):

- Agent index files
- Individual agent JSON files
- Schema definitions
- All language variants

> \[!NOTE]: This step is optional during development. The `/public` directory is automatically generated during deployment (e.g., by GitHub Actions). You typically only need to run `bun run format` locally.

---

## File Structure

### Source Directory (`/src`)

```
/src/
  ├── airdrop-hunter.json
  ├── alpha-leak-detector.json
  ├── defi-yield-farmer.json
  └── ... (41 agents total)
```

Each agent is a single JSON file in English (en-US).

### Locales Directory (`/locales`)

After running `bun run format`:

```
/locales/
  ├── airdrop-hunter/
  │   ├── index.json       (en-US)
  │   ├── index.ar.json
  │   ├── index.zh-CN.json
  │   └── ... (18 language files)
  │
  ├── alpha-leak-detector/
  │   ├── index.json
  │   └── ... (18 language files)
  │
  └── ... (41 agent folders)
```

Each agent gets its own folder with 18 translation files.

### Public Directory (`/public`)

**Generated by `bun run build` - Not in Git**

The `/public` directory is:

- ✅ **Generated** by the build command
- ✅ **Gitignored** (listed in `.gitignore`)
- ✅ **Optional** for development - only needed for deployment
- ✅ **CDN-ready** output for serving agents

After running `bun run build`:

```
/public/
  ├── index.json           (Main agent index - English)
  ├── index.zh-CN.json     (Chinese index)
  ├── index.ja-JP.json     (Japanese index)
  └── agents/
      ├── airdrop-hunter.json
      ├── airdrop-hunter.ar.json
      └── ... (all agents × 18 languages)
```

> \[!IMPORTANT]: Don't commit `/public` to Git. It's automatically generated during deployment.

---

## Configuration

### Translation Configuration (`.i18nrc.js`)

The workflow is configured via `.i18nrc.js`:

```javascript
module.exports = {
  // Fields to translate
  selectors: [
    'meta.title',
    'meta.description',
    'meta.tags',
    'meta.category',
    'config.systemRole',
    'config.openingMessage',
    'config.openingQuestions',
    'examples',
    'summary',
  ],

  // Source language
  entryLocale: 'en-US',

  // Target languages (18 total)
  outputLocales: [
    'en-US',
    'ar',
    'bg-BG',
    'zh-TW',
    'ru-RU',
    'ja-JP',
    'zh-CN',
    'ko-KR',
    'fr-FR',
    'tr-TR',
    'es-ES',
    'pt-BR',
    'de-DE',
    'it-IT',
    'nl-NL',
    'pl-PL',
    'vi-VN',
    'fa-IR',
  ],

  // OpenAI model configuration
  modelName: 'gpt-4.1-nano',
  temperature: 0.5,
  concurrency: 18,
};
```

### What Gets Translated

The following fields are automatically extracted and translated:

| Field                     | Description              | Example                             |
| ------------------------- | ------------------------ | ----------------------------------- |
| `meta.title`              | Agent display name       | "DeFi Yield Farmer"                 |
| `meta.description`        | Short description        | "Optimize yield farming strategies" |
| `meta.tags`               | Searchable keywords      | \["defi", "yield", "farming"]       |
| `meta.category`           | Agent category           | "defi", "programming", etc.         |
| `config.systemRole`       | Main prompt/instructions | "You are an expert..."              |
| `config.openingMessage`   | Welcome message          | "Hello! I can help you..."          |
| `config.openingQuestions` | Suggested questions      | \["How do I...", "What is..."]      |
| `examples`                | Conversation examples    | User/assistant dialogues            |
| `summary`                 | Extended description     | Full agent capabilities             |

### What Does NOT Get Translated

- `identifier`: File name identifier (e.g., `defi-yield-farmer`)
- `author`: GitHub username
- `schemaVersion`: Version number
- `createdAt`: Timestamp
- `avatar`: Emoji or icon
- `homepage`: URL
- Role fields in examples: `"role": "user"`, `"role": "assistant"` remain in English

---

## Running the Workflow

### Available Commands

```bash
# Main workflow commands
bun run format # Format agents + translate to 18 languages
bun run build  # Build public distribution
bun run test   # Validate agent JSON structure

# Translation-specific commands
bun run i18n:validate # Check translation language accuracy
bun run i18n:fix      # Validate and fix translation issues
bun run i18n:clean    # Remove invalid translation files

# Development commands
bun run lint       # Lint TypeScript files
bun run type-check # TypeScript type checking
bun run prettier   # Format all code files
```

### Typical Development Workflow

1. **Create or edit an agent**

   ```bash
   vim src/my-new-agent.json
   ```

2. **Format and translate**

   ```bash
   bun run format
   ```

   - Watch for console output
   - Check for any translation errors
   - Review generated files in `/locales`

3. **Validate translations**

   ```bash
   bun run i18n:validate
   ```

   - Ensures translations are in correct language
   - Reports confidence scores

4. **Build distribution**

   ```bash
   bun run build
   ```

   - Creates `/public` directory
   - Ready for deployment

5. **Commit changes**
   ```bash
   git add .
   git commit -m "feat: add my-new-agent with 18 language support"
   git push
   ```

---

## Understanding the Process

### Translation Pipeline

The translation system uses OpenAI's GPT models with specialized prompts:

1. **Extract**: Identifies translatable fields based on `.i18nrc.js` selectors
2. **Prepare**: Structures content as JSON for AI processing
3. **Translate**: Calls OpenAI with language-specific instructions
4. **Parse**: Converts AI response back to JSON (with fallback parsing)
5. **Merge**: Combines translations with existing content
6. **Validate**: Verifies translation language accuracy
7. **Save**: Writes locale-specific files

### OpenAI Translation Prompt

The system uses this specialized prompt:

```
Translate the i18n JSON file to {target_language} according to BCP 47 standards.

Rules:
- Keep key names unchanged
- Output must be valid JSON
- Keep "role" fields unchanged (user, assistant, system, function)
- Only translate "content" fields and text content
- Return only JSON, no explanations
```

### Incremental Translation

The system intelligently handles updates:

- **First Run**: Translates all fields for all languages
- **Subsequent Runs**: Only translates new or modified fields
- **Merge Strategy**: Uses `lodash.merge` to combine old + new translations
- **Cost Optimization**: Avoids re-translating existing content

Example:

```javascript
// First format run
{
  "meta.title": "DeFi Farmer",
  "meta.description": "Optimize yields"
}
// → Translates both fields to 18 languages

// You add a new field
{
  "meta.title": "DeFi Farmer",
  "meta.description": "Optimize yields",
  "config.openingMessage": "Hello!" // NEW
}
// → Only translates openingMessage to 18 languages
// → Keeps existing translations for title and description
```

---

## Translation Features

### 1. **Automatic Content Generation**

If your agent is missing content, the workflow auto-generates:

- **Category**: AI determines the best category (defi, programming, etc.)
- **Summary**: Extended description of capabilities
- **Examples**: Sample conversation dialogues
- **Opening Message**: Welcome message for users
- **Opening Questions**: Suggested starter questions

### 2. **Intelligent Retries**

- **Max Retries**: 4 attempts per API call
- **Exponential Backoff**: Automatic retry with delays
- **Dirty JSON Parsing**: Fallback parser if AI returns invalid JSON

### 3. **Concurrent Processing**

- **Concurrency**: 18 parallel translation jobs
- **Efficiency**: Translates all languages simultaneously
- **Speed**: Completes 18 languages in \~30-60 seconds per agent

### 4. **Language Detection**

Uses the `@yutengjing/eld` library to verify:

- Translation is in the correct language
- Confidence score meets threshold
- Flags mismatched languages

### 5. **Ignore List**

Create `.i18nignore` to skip problematic files:

```
# Skip validation for specific files
locales/my-agent/index.ar.json
locales/another-agent/index.fa-IR.json
```

---

## Validation & Quality Control

### Translation Validation

```bash
bun run i18n:validate
```

Checks each translation file:

- ✅ Detects actual language of content
- ✅ Compares against expected language code
- ✅ Reports confidence scores (0-1)
- ✅ Identifies mismatched languages

Example output:

```
✓ locales/airdrop-hunter/index.zh-CN.json [Confidence: 0.95]
✗ locales/airdrop-hunter/index.ar.json [MISMATCH: Expected ar, got en]
```

### Fix Mode

```bash
bun run i18n:fix
```

- Validates all files
- Attempts to recover from issues
- Re-translates failed files
- Updates ignore list for persistent failures

### Clean Mode

```bash
bun run i18n:clean
```

- Validates all files
- **Deletes** files that fail validation
- Removes low-confidence translations
- Use with caution!

---

## GitHub Actions Integration

### Automated Workflow

The project includes `.github/workflows/format.yml` that:

1. Triggers on Pull Requests
2. Installs Bun and dependencies
3. Runs `bun run format` with OpenAI API
4. Validates translations with `bun run i18n:fix`
5. Auto-commits changes back to the PR

### Workflow File

```yaml
name: Format

on:
  pull_request:
  workflow_dispatch:

jobs:
  update-i18n:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install bun
        uses: oven-sh/setup-bun@v1

      - name: Install deps
        run: bun i

      - name: Run format
        run: bun run format
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
          OPENAI_PROXY_URL: ${{ secrets.OPENAI_PROXY_URL }}

      - name: Run fix
        run: bun run i18n:fix

      - name: Commit changes
        run: |
          git config user.name "bot"
          git config user.email "bot@users.noreply.github.com"
          git add .
          git commit -m "🤖 chore: Auto format and add i18n json files"
          git push
```

### Required Secrets

Set these in your GitHub repository settings:

| Secret             | Purpose                   | Required    |
| ------------------ | ------------------------- | ----------- |
| `OPENAI_API_KEY`   | OpenAI API authentication | ✅ Yes      |
| `OPENAI_PROXY_URL` | Custom OpenAI endpoint    | ❌ Optional |
| `GH_TOKEN`         | Git push permissions      | ✅ Yes      |

---

## Troubleshooting

### Issue: "OPENAI_API_KEY is not set"

**Cause**: Environment variable is missing

**Solution**:

```bash
# Create .env file
echo "OPENAI_API_KEY=sk-your-key" > .env

# Or export directly
export OPENAI_API_KEY=sk-your-key
```

### Issue: Translation API fails repeatedly

**Cause**: Rate limiting, invalid API key, or network issues

**Solutions**:

1. Check API key validity
2. Verify API credits remaining
3. Check `OPENAI_PROXY_URL` if using custom endpoint
4. Reduce concurrency in `.i18nrc.js`:
   ```javascript
   concurrency: 5, // Lower from 18
   ```

### Issue: Translation is in wrong language

**Cause**: AI model generated incorrect language

**Solutions**:

1. Run validation:
   ```bash
   bun run i18n:validate
   ```
2. Check confidence scores
3. Re-translate specific agent:
   ```bash
   # Delete locale folder and re-run
   rm -rf locales/agent-name/
   bun run format
   ```

### Issue: JSON parsing errors

**Cause**: AI returned invalid JSON

**Solution**: The system has automatic fallbacks:

1. Standard JSON.parse()
2. Dirty JSON parser (lenient parsing)
3. Logs the raw response for debugging

Check console output for details.

### Issue: Translations are incomplete

**Cause**: Process was interrupted or API failed

**Solution**:

```bash
# Re-run format (incremental detection will only translate missing)
bun run format

# Or delete locale folder to start fresh
rm -rf locales/agent-name/
bun run format
```

### Issue: Exceeding OpenAI costs

**Cause**: Large agents or many agents

**Solutions**:

1. Use a more cost-effective model:
   ```javascript
   // .i18nrc.js
   modelName: 'gpt-3.5-turbo', // Cheaper than gpt-4
   ```
2. Reduce unnecessary text in `systemRole`
3. Process agents individually:
   ```bash
   # Temporarily move agents out of /src
   mkdir temp && mv src/*.json temp/
   # Move back one agent at a time
   mv temp/my-agent.json src/
   bun run format
   ```

---

## Advanced Topics

### Custom Translation Models

Edit `.i18nrc.js` to use different models:

```javascript
module.exports = {
  modelName: 'gpt-4-turbo', // More accurate
  // modelName: 'gpt-3.5-turbo',   // More cost-effective
  // modelName: 'gpt-4o',          // Latest model
  temperature: 0.5, // Lower = more consistent
  concurrency: 18, // Parallel jobs
};
```

### Adding New Languages

To add a new language:

1. Edit `.i18nrc.js`:

   ```javascript
   outputLocales: [
     'en-US',
     // ... existing languages
     'hi-IN', // Add Hindi
   ],
   ```

2. Run format:

   ```bash
   bun run format
   ```

3. Verify language detection works:
   ```bash
   bun run i18n:validate
   ```

### Translation Field Customization

Customize which fields get translated:

```javascript
// .i18nrc.js
selectors: [
  'meta.title',
  'meta.description',
  'config.systemRole',
  // Add custom fields:
  'customField.text',
  'additionalPrompts.greeting',
],
```

### Manual Translation Override

To provide manual translations:

1. Run format to generate all files
2. Edit specific locale file manually:
   ```bash
   vim locales/my-agent/index.fr-FR.json
   ```
3. Add to ignore list to prevent overwrite:
   ```bash
   echo "locales/my-agent/index.fr-FR.json" >> .i18nignore
   ```

### Debugging Translation Issues

Enable debug mode:

```bash
DEBUG=true bun run format
```

View detailed logs:

- OpenAI API requests
- Response parsing
- Merge operations
- File operations

---

## Best Practices

### 1. **Write Clear English Source Content**

Good translations start with clear source text:

- ✅ Use simple, direct language
- ✅ Avoid idioms and slang
- ✅ Be specific and technical when needed
- ❌ Don't use ambiguous phrasing

### 2. **Test After Changes**

Always validate after updates:

```bash
bun run format && bun run i18n:validate && bun run build
```

### 3. **Monitor API Costs**

- Track OpenAI API usage
- Use cheaper models for testing
- Process agents incrementally for large changes

### 4. **Commit Locale Files**

- ✅ Commit all `/locales` files to Git
- ✅ Track translation changes in PRs
- ✅ Review AI-generated translations

### 5. **Version Control**

When updating an agent:

```bash
# Before changes
git add src/my-agent.json

# After format
git add locales/my-agent/
git commit -m "feat: update my-agent + translations"
```

---

## Summary

The 18 Languages i18n workflow provides:

- 🌍 **Automatic translation** to 18 languages
- 🚀 **Fast processing** with concurrent API calls
- 💰 **Cost-effective** with incremental updates
- ✅ **Quality assurance** with language validation
- 🔄 **CI/CD integration** with GitHub Actions
- 📦 **CDN-ready output** for global distribution

Simply create your agent in English, run `bun run format`, and your agent is instantly available to users worldwide in their native language.

---

## Additional Resources

- [OpenAI API Documentation](https://platform.openai.com/docs)
- [BCP 47 Language Tags](https://www.rfc-editor.org/info/bcp47)
- [Contributing Guide](./CONTRIBUTING.md)
- [Agent Guide](./AGENT_GUIDE.md)
- [Troubleshooting](./TROUBLESHOOTING.md)

---

**Questions or Issues?**

- 📝 Open an issue on GitHub
- 💬 Check [FAQ.md](./FAQ.md)
- 🐛 Report bugs with detailed logs