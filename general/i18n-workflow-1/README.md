# I18N WORKFLOW

> > Comprehensive guide to the automated internationalization (i18n) workflow that translates your AI agents into 18 languages using OpenAI GPT models.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
| `es-ES` | Spanish         

*[truncated — see source for full prompt]*